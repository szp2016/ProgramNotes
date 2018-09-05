## 本地git关联github
1.输入你的github注册邮箱,生成本地ssh key
> $ ssh-keygen -t rsa -C "your_email@youremail.com"  


![avatar](https://github.com/szp2016/ProgramNotes/blob/master/image/github%E6%B7%BB%E5%8A%A0SSH%20key.png)       


2.然后成功后会在User文件夹对应的用户下创建.ssh文件夹，其中有一个id_rsa.pub文件，我们复制其中的key,进入 Account Settings（账户配置），左边选择SSH and GPG Keys选项。 
其中的title随便填，下面的粘贴在你电脑上生成的key。 

![avatar](https://github.com/szp2016/ProgramNotes/blob/master/image/%E5%88%9B%E5%BB%BASSH%20key.png)  

3.验证是否绑定本地成功，在git-bash中验证，输入指令：  
> $ ssh -T git@github.com  


如果第一次执行该指令，则会提示是否continue继续，如果我们输入yes就会看到成功信息：   

![avatar](https://github.com/szp2016/ProgramNotes/blob/master/image/%E9%AA%8C%E8%AF%81%E6%98%AF%E5%90%A6%E6%88%90%E5%8A%9F.png)  

4.由于GitHub每次执行commit操作时，都会记录username和email，下面进行设置：

> $ git config --global user.name  "name"//你的GitHub登陆名  
> $ git config --global user.email "123@163.com"//你的GitHub注册邮箱  


![avatar](https://github.com/szp2016/ProgramNotes/blob/master/image/%E8%AE%BE%E7%BD%AE%E6%8F%90%E4%BA%A4%E7%9A%84%E7%94%A8%E6%88%B7%E5%90%8D%E5%92%8C%E9%82%AE%E7%AE%B1.png)


5.在github上新建一个仓库，并添加一个README.md文件，并pull到本地：  
> $ git pull "仓库的ssh链接"  


6.常用git命令  
> git init //把这个目录变成Git仓库    
git add README.md //文件添加到仓库  
git add . //不但可以跟单一文件，还可以跟通配符，添加当前目录下所有文件   
git commit -m "first commit" //把文件提交到本地仓库  
git remote add origin git@github.com:yourname/youremail.git //关联远程仓库  
git push -u origin master //上传到远程仓库
