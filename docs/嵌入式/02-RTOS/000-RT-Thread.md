# 联网
## esp8266
### 遇见的问题
1.没有`AT+CIPDNS_CUR?`命令  
   ![error-rtthread-cipdns_cut](图片/error-rtthread-cipdns_cut.png)
解决：  更新esp8266固件  

 * 使用安信可固件  
   [固件下载](https://docs.ai-thinker.com/esp8266)  
     使用`博安通 AT 固件`固件  
     ![ai-bat](../01-单片机/图片/00-ESP/ai-bat.png) 

 * 使用乐鑫固件  
     [固件下载](https://www.espressif.com/zh-hans/support/download/at?keys=)

     [官方文档说明](https://docs.espressif.com/projects/esp-at/en/latest/AT_Binary_Lists/index.html)

     网上说使用ESP8266-IDF-AT_V2.1.0.0版本

     官网说使用该版本下的factory_xxx.bin，烧录在0地址下

     本人烧录未成功
