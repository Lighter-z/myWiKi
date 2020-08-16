#WiKi搭建
* [中文教程](https://markdown-docs-zh.readthedocs.io/zh_CN/latest/)
  1.系统
* Ubuntu系统  
   ```
   sudo apt-get install mkdocs
   ```

* Windows系统  
   ` pip install mkdocs`

2.环境  

2.1安装python  

2.2安装pip  

```
  pip install --upgrade pip
```

  * 如果出错使用下面命令  
    ```
    pip install lxml
    ```

3.安装MKDocs  
    ​```
    pip install mkdocs
    ​```

* 确认是否安装正确  
    ```
    mkdocs --version
    ```

* 创建一个WiKi  
    ```
    mkdocs new myWiKi
    cd myWiKi
    ```
    * docs文件夹下存放的就是自己写的Markdown文章，系统默认会生成一个index.md文件  
    * mkdocs.yml是wiki网站的配置文件（主题、目录、语言等  ）  

* 预览WiKi(启动mkdocs服务器)  
```
mkdocs serve
```
    * 本地访问：在浏览器中输入127.0.0.1:8000访问wiki    

5.将WiKi站点托管到Github    

  * 在Github上创建一个新仓库(仓库名要与你的wiki文件夹名一致)  
  * 初始化本地仓库(你的wiki文件夹)，添加远程仓库，提交本地修改并推送到远程仓库    
  ```
  cd myWiKi
  git init
  git git remote add origin git@github.com:Lighter-z/myWiKi.git
  git add .
  git commit -m "myWiKi"
  git push origin master
  ```
  * 将站点部署到Github上  
  ```
  mkdocs gh-deploy
  ```
  *  现在你的wiki站点（HTML文件）在gh-pages分支，你的wiki站点（markdown文件）在master分支。  
  *  通过以下网址访问你的WiKi  
  ```
  https://user_name.github.io/repository_name
  https://lighter-z.github.io/myWiKi/
  ```

6.其他命令

   * `mkdocs new '工程名'` 创建新的MkDocs工程

   * `mkdocs serve` 运行内建的开发服务器

   * `mkdocs build` 构建MkDocs文档

   * `mkdocs gh-deploy` 将文档部署到GitHub页面上

   * `mkdocs json` 将MkDocs文档构建成JSON文件

   * 若有文件被从源码中移除了, 但是相关的文档仍残留在 `site` 目录中. 在构建命令中添加 `--clean` 参数即可移除这些文档.

     ```
     mkdocs build --clean
     ```

# mkdocs-material

1.安装

  `pip install mkdocs mkdocs-material`  

* 如果下载过慢，可更换安装源为豆瓣  
  `pip install --trusted-host pypi.douban.com -i http://pypi.douban.com/simple/ mkdocs mkdocs-material`
