-----------------------------------------------------
如果您嫌命令麻烦：
可以使用这个一键部署：

一键部署，请点击下方的"Deploy to Heroku"按钮， 具体步骤请参考 [WIKI](https://github.com/gfw-breaker/heroku-node-proxy/wiki)。

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)


-----------------------------------------------------
**手动部署：**
**为了您一次能安装成功，请按照以下步骤逐步操作：**


> 1.点击fork这个项目。操作成功后跳转到您的you2php项目页面。

![pH5t3D.png](https://s1.ax1x.com/2018/01/25/pH5t3D.png)

> 2.编辑web/config.php文件，修改里面的第三行，填入您申请的youtube api key。其他几行也可以修改。看注释

![pHhWRg.png](https://s1.ax1x.com/2018/01/25/pHhWRg.png)
![pHhRJS.png](https://s1.ax1x.com/2018/01/25/pHhRJS.png)

> 3.执行命令创建您的heroku应用：

ps：记住把下面命令中的第一条中的you2php改成您的Github用户名，(如：`git clone https://github.com/You-username/you2php-heroku.git` )因为您需要提交您的仓库代码。第三条中{You APP Name}改成您的heroku应用域名前缀名（不需要加花括号）。


```
git clone https://github.com/You2php/you2php-heroku.git

cd you2php-heroku

heroku create {You APP Name}

git push heroku master

heroku ps:scale web=1

heroku open
```


ps：执行上面的命令需要在您的计算机上安装heroku CLI（下载地址：https://devcenter.heroku.com/articles/getting-started-with-php#set-up）

站点加锁
如果不想让您的You2PHP站点让其他人访问，可以对站点使用密码保护方法——使用htpasswd文件来实现。访问页面之后会弹出一个输入框，需要输入正确的用户名和密码才能浏览网页上的内容，否则会出错。同时搜索引擎无法收录!

1.首先，需要创建一个名为.htpasswd的文件， 将这个.htpasswd文件存放You2PHP的安装目录下。这个文件用于存储用户名和加密后的密码。比如用户名为admin，密码为123456，那么在.htpasswd文件中的内容可能就是这样的：

admin:9dKtKHPyz51Vs
用户名后紧跟的是密码，用:隔开。而且密码是加密后的密文。上传这个.htpasswd文件You2PHP的安装目录下。有一个在线生成.htpasswd文件的网站：http://www.htaccesstools.com/htpasswd-generator
通过这个地址可以生成加密后的密码。

2.创建一个新的.htaccess文件，将这个.htaccess文件存放You2PHP的安装目录下。并编辑这个文件，写入如下内容：

AuthName "Restricted Area"
AuthType Basic
AuthUserFile /home/hosting/public_html/.htpasswd
AuthGroupFile /dev/null
require valid-user
注意，需要把AuthUserFile后面/home/hosting/public_html/改成您的You2PHP站点绝对安装路径（如果装在子目录，那么应该加上子目录路径，如 /home/hosting/public_html/youtube）

3.现在打开您的You2PHP站点，会弹出一个这样的框框，需要填写正确的用户名和密码才能浏览！可以通过修改.htpasswd文件修改密码。
