[野火emWin教程](https://ebf-emwin-tutorial.readthedocs.io/zh_CN/latest/index.html)

# 文本显示

## 代码示例

```C
static void TextInit(void) {
	U8 i;

    /* 设置背景色 */
    GUI_SetBkColor(GUI_BLUE);
    GUI_Clear();

    /* 设置字体大小 */
    GUI_SetFont(GUI_FONT_32_1);
    GUI_DispStringAt("STemWIN@EmbeddedFire STM32F429", 10, 10);

    //显示文本
    GUI_GotoXY(15, 100);
    GUI_DispString("hello world");

    /* 画线 */
    GUI_SetPenSize(10);
    GUI_SetColor(GUI_RED);
    GUI_DrawLine(10, 100, 10, 200);
    GUI_SetColor(GUI_GREEN);
    GUI_DrawLine(30, 100, 100, 100);

    /* 绘制文本 */
    GUI_SetBkColor(GUI_BLACK);
    GUI_SetColor(GUI_WHITE);
    GUI_SetFont(GUI_FONT_24B_ASCII);
    /* 正常模式 */
    GUI_SetTextMode(GUI_TM_NORMAL);
    //居中显示字符串
    GUI_DispStringHCenterAt("GUI_TM_NORMAL", 400, 120);
    /* 反转显示 */
    GUI_SetTextMode(GUI_TM_REV);
    GUI_DispStringHCenterAt("GUI_TM_REV", 400, 120 + 24);
    /* 透明文本 */
    GUI_SetTextMode(GUI_TM_TRANS);
    GUI_DispStringHCenterAt("GUI_TM_TRANS", 400, 120 + 24 * 2);
    /* 异或文本 */  
    GUI_SetTextMode(GUI_TM_XOR);  //文本反转背景
    GUI_DispStringHCenterAt("GUI_TM_XOR", 400, 120 + 24 * 3);
    /* 透明反转文本 */
    GUI_SetTextMode(GUI_TM_TRANS | GUI_TM_REV);
    GUI_DispStringHCenterAt("GUI_TM_TRANS | GUI_TM_REV", 400, 120 + 24* 4);

    /* 在矩形区域内显示文本 */
    GUI_SetFont(GUI_FONT_24B_ASCII);
    GUI_SetTextMode(GUI_TM_TRANS);
    for (i = 0; i < 3; i++) {
        GUI_SetColor(GUI_WHITE);
        GUI_FillRectEx(&rect1);
        GUI_SetColor(GUI_RED);
        GUI_DispStringInRectWrap(acText, &rect1, GUI_TA_LEFT, aWm[i]);  //在指定矩形中显示包含在矩形中的字符串，带换行模式
        rect1.x0 += 156;
        rect1.x1 += 156;
    }

    for (i = 0; i < 4; i++) {
        GUI_SetColor(GUI_WHITE);
        GUI_FillRectEx(&rect2);
        GUI_SetColor(GUI_RED);
        switch (i) {
            //在指定矩形中显示包含在矩形中的字符串，带换行 和旋转 模式
            case 0: GUI_DispStringInRectWrapEx(acText, &rect2, GUI_TA_LEFT, aWm[i], GUI_ROTATE_0); break;
            case 1: GUI_DispStringInRectWrapEx(acText, &rect2, GUI_TA_LEFT, aWm[i], GUI_ROTATE_180); break;
            case 2: GUI_DispStringInRectWrapEx(acText, &rect2, GUI_TA_LEFT, aWm[i], GUI_ROTATE_CW); break;
            case 3: GUI_DispStringInRectWrapEx(acText, &rect2, GUI_TA_LEFT, aWm[i], GUI_ROTATE_CCW); break;
        }
        rect2.x0 += 156;
        rect2.x1 += 156;
    }
}

```



# 数值显示

## 代码示例

### 十进制数据显示

```c
static void ValueInit(void) {
    /* 设置背景色 */
    GUI_SetBkColor(GUI_YELLOW);
    GUI_Clear();

    GUI_SetFont(GUI_FONT_24B_ASCII);
    GUI_SetColor(GUI_WHITE);

    GUI_DispStringAt("GUI_DispDec():", 0, 0);
    GUI_DispNextLine();
    //GUI_DispDec()当前位置显示十进制数 
    //第一个参数：要显示的数据；第二个参数：显示多少位字符
    //当显示的数据长度<字符位数，则前面补零显示
    GUI_DispDec(444, 6);  
    GUI_GotoX(12 * 9);  //x坐标移到12*9的位置
    GUI_DispDec(-12345, 6);

    //GUI_DispDecAt()指定位置显示十进制数
    GUI_DispStringAt("GUI_DispDecAt():", 0, 24 * 2);
    GUI_DispDecAt(12345, 0, 24 * 3, 6);
    GUI_DispDecAt(-12345, 12*9, 24 * 3, 6);

    //GUI_DispDecMin()当前为位置显示最小位数的十进制数
    //不需要指定数据长度，会自动使用最小长度值
    GUI_DispStringAt("GUI_DispDecMin():", 0, 24 * 4);
    GUI_DispNextLine();
    GUI_DispDecMin(1234); 
    GUI_GotoX(12 * 9);
    GUI_DispDecMin(-12345);

    //当前位置显示指定位数的十进制数，带小数点
    GUI_DispStringAt("GUI_DispDecShift():", 0, 24 * 6);
    GUI_DispNextLine();
    GUI_DispDecShift(12345, 7, 2);
    GUI_GotoX(12 * 9);
    GUI_DispDecShift(-12345, 7, 2);

    //当前位置显示十进制数 
    //位数不足时，用空格代替前面的0
    GUI_DispStringAt("GUI_DispDecSpace():", 0, 24 * 8);
    GUI_DispNextLine();
    GUI_DispDecSpace(123, 6);

    //当前位置显示指定位数的十进制数，带符号
    GUI_DispStringAt("GUI_DispSDec():", 0, 24 * 10);
    GUI_DispNextLine();
    GUI_DispSDec(12345, 6);

    //当前位置显示指定位数的十进制长数，带符号，小数点
    GUI_DispStringAt("GUI_DispSDecShift():", 0, 24 * 12);
    GUI_DispNextLine();
    GUI_DispSDecShift(-12345, 7, 2);
}
```

* 所有十进制显示函数的数值类型都是有符号int型， 即可输入的数值范围为−231−231至231−1231−1。使用这些函数需要注意以下问题：

      (1) 待显示数值的最高位不能是0， 否则无法显示。例如需要显示的数是012345，不管指定的显示位数设置为多少，函数都无法显示。

      (2) 指定的显示位数必须大于等于待显示数值的位数，否则无法显示。例如待显示数为12345， 当指定显示位数小于5时，函数无法显示，大于5时，会在待显示数值的最高位补零，其中GUI_DispDecSpace()函数会在最高位补空格。

      (3) 如果待显示数值中含有负号或小数点，包括使用GUI_DispDecShift()和GUI_DispSDecShift()， 在指定显示位数时需要把这些符号也计算在内，否则函数无法正常显示。


