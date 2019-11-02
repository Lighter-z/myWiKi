#WiKi搭建
##1. 安装MKDocs
###1.1 Ubuntu系统
`sudo apt-get install mkdocs`
###1.2 Windows系统
`sudo apt-get install mkdocs`
####安装python
####安装pip  
`pip install --upgrade pip`  
如果出错，尝试以下命令  
`pip install lxml`  
####安装MKDocs  
`pip install mkdocs`  
###1.3 确认是否安装正确  
`mkdocs --version`  
##2. 创建一个WiKi  
```
mkdocs new myWiKi
cd myWiKi
```  
docs文件夹下存放的就是自己写的Markdown文章，系统默认会生成一个index.md文件  
mkdocs.yml是wiki网站的配置文件（主题、目录、语言等）  
##3. 预览WiKi  
启动mkdocs服务器  
`mkdocs serve`  
在浏览器中输入127.0.0.1:8000访问wiki  
##4. 将你的WiKi站点托管到Github  
在Github上创建一个新仓库(仓库名要与你的wiki文件夹名一致)  
初始化本地仓库(你的wiki文件夹)，添加远程仓库，提交本地修改并推送到远程仓库  
```
cd myWiKi
git init
git git remote add origin git@github.com:Lighter-z/myWiKi.git
git add .
git commit -m "myWiKi"
git push origin master
```  
将站点部署到Github上  
`mkdocs gh-deploy`  
现在你的wiki站点（HTML文件）在gh-pages分支，你的wiki站点（markdown文件）在master分支。  
可以通过以下网址访问你的WiKi  
https://user_name.github.io/repository_name  



