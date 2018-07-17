Hexo连接搭建自己的博客(Mac) - 转
===

1. 安装前，电脑中必须有:

	- [Node.js](https://nodejs.org/en/download/)

	- [Git](https://git-scm.com/downloads)

2. 打开命令行(Terminal)
	
		 $ sudo npm install -g hexo-cli
	
	> 如果电脑中还有未安装的程序，需要根据提示完成安装
	
3. 登陆 [github.com](https://github.com)
	
	* 点击 ``Create a new repository``
	
	* Repository name 输入 ``你的用户名.github.io``
	
	* 勾选 ``Initialize this repository with a README``
	
	* 点击 ``Create repository``
	
4. 点击 ``Insights`` 右边的 ``Setting``

	找到``GitHub Page``
	
	在 ``Source`` 一栏选择 ``master branch`` 并点击 ``Save``
	
5. 回到命令行，创建一个自己的博客文件并进入

		$ cd ~/Document
		$ mkdir blog
		$ cd blog
		
6. 安装 Hexo

		$ npm install hexo -g
		
	安装完成后，输入
	
		$ hexo -v
		
	检查是否安装成功
	
	如果安装成功，则进行 hexo 初始化
	
		$ hexo init
		
7. 安装所需组件

		$ npm install
		
8. 首次部署和体验 hexo

		$ hexo g
		
		$ hexo s // 如果页面一直无法跳转，可能端口被占用，此时先control + c停止服务器，然后输入hexo server -p 端口号 来改变端口
		
9. 设置``git``的``user.name``和``user.email``

		$ git config --global user.name 你的git名
		$ git config --global user.email 你的github绑定邮箱
		
10. 设置 **ssh**

		$ cd ~/.ssh // 如果没有此文件夹则使用 $ mkdir ~/.ssh创建
		$ ssh-keygen -t rsa -C "你的github绑定邮箱"
	
	> 连续按三个回车
		
		$ eval "$(ssh-agent -s)" // 添加密钥到ssh-agent
		$ ssh-add ~/.ssh/id_rsa // 添加生成的SSH key到ssh-agent
		
11. 登陆Github，点击头像下面的``settings``，选择左边栏的``SSH and GPG keys``，点击右边的``New SSH key``

	输入Title
	
	把 ``~/.ssh/id_rsa.pub`` 文件中的内容复制上去

12. 在命令行中输入

		ssh -T git@github.com
		
	如果``Hi``后面看到你的用户名，说明配置成功
	
13. 配置``Deployment``

	在你之前创建的博客文件夹中找到_config.yml文件进行修改(文件末尾):
	
		deploy:
			type: git
			repository: git@github.com:你的github用户名/你的github用户名.github.io.git
			branch: master
			
	注意冒号之后都有一个空格，注意严格缩进
	
14. 新建一篇博客

	回到命令行，``cd`` 到你的博客文件夹中
	
	然后执行
	
		$ hexo new post "博客名"
		
	安装git发布依赖
	
		$ npm install hexo-deployer-git --save
		
	部署：
		
		$ hexo d -g
		
15. 访问你的博客

	[**http://你的用户名.github.io**](http://YapAmbition.github.io)
	

	
