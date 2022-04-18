##### 公钥和私钥的作用

​	**为什么要配置公钥和私钥：**

[Git](https://link.jianshu.com?t=http://lib.csdn.net/base/git)使用https协议，每次pull, push都要输入密码，相当的烦。
 使用[git](https://link.jianshu.com?t=http://lib.csdn.net/base/git)协议，然后使用ssh密钥。这样可以省去每次都输密码。

公钥我们一般是给服务器的,他们到时候在权限中加入我给的公钥,然后当我从远地仓库中下载项目的时候,我在`git clone xxx`的时候，那个服务器我通过他的绑定的公钥来匹配我的私钥，这个时候,如果匹配,则就可以正常下载,如果不匹配,则失败.

大多数 Git 服务器都会选择使用 SSH 公钥来进行授权。系统中的每个用户都必须提供一个公钥用于授权，没有的话就要生成一个。



> ""大多数 Git 服务器都会选择使用 SSH 公钥来进行授权。系统中的每个用户都必须提供一个公钥用于授权，没有的话就要生成一个""
>
> 而Git服务器可以个人搭建,  比如在公司中的项目的话,是不是公司搭建一个git服务器, 然后上传公钥到这个git服务器上来进行项目仓库的托管.
>
> 毕竟github也就是一个托管git仓库的平台,本质应该也就是个git服务器吧,所以github需要上传密钥,和本地的私钥来配对从而进行pull和push吧.



1. 但是为什么我没有添加公钥,本地也没有私钥,为什么我还能git clone 别人的仓库呢?

​		答:

​	 			原来我之前一直用的是https来git clone 的,当然就不需要公钥和密钥了.

​				但是,可以看到,使用ssh时,就提示了我没有公钥,不能用

<center>
<img src="C:\Users\Ryz\AppData\Roaming\Typora\typora-user-images\image-20220414190941948.png" width=300/>
<img src="C:\Users\Ryz\AppData\Roaming\Typora\typora-user-images\image-20220414191043945.png" width=300/>
</center>

2. 但是开始不是说https 要输密码吗,为啥我用 https的链接来git clone 时没有一次让我输密码啊

​	查了一下果然有人和我一样的疑问:

<img src="C:\Users\Ryz\AppData\Roaming\Typora\typora-user-images\image-20220414192653132.png" width=700/>

创建一个私有仓库试一下:

![image-20220414195037545](C:\Users\Ryz\AppData\Roaming\Typora\typora-user-images\image-20220414195037545.png)

果然弹出了登陆界面:

![image-20220414195150181](C:\Users\Ryz\AppData\Roaming\Typora\typora-user-images\image-20220414195150181.png)





3. 还有一个问题,我暂时没法搞:因为要多人协同:

> ​		比如 我创建了一个私有仓库,然后有几个协同工作者,他们都设置了ssh公钥和密钥,那么就可以直接用ssh来不输入密码来pull push 项目了,
>
> 但是如果一个人他参与多个项目,都是私有仓库的话,该怎么区别他们的ssh公钥和私钥呢, 设置公钥的时候也只是提供了邮件地址,难道创建私有仓库时会需要添加每个人generate的ssh公钥吗?

> ​	有可能提供的邮箱就是创建私有仓库那个人的邮箱,这样每个人都通过创建者的邮箱来生成公钥私钥pair,应该就可以吧,但是如果创建者有多个仓库呢,
>
> cao ,可能公钥私钥pair 根本就不是用在区别每个私有仓库的吧!!!

> ​	可能private 仓库只是设置了对他人不可见吧,  所以有了公钥就可以在github随意pull push公有仓库(不要也行啊), 同时可以不输入密码来pull push 所有参与的私有仓库吧,应该是 

> 显然现在学的还太少,只自己在这思考有点没什么用!!

**2022/4/16** 	

> 我自己创建了俩github的账号: A 和 B
>
> 而我的笔记本上存储的只有账号A的公钥私钥pair,
>
> 要分清楚git 和 GitHub是分离的, 所以即使我登陆的是账号B,
>
> 我 在本地上 git clone A的仓库, 我可以随意的push 和 pull,因为本地存储的就是账号A的公钥私钥pair
>
> 而如果我git clone B的仓库,我是不可以git push的,只能通过 pull request 来协同工作了.
>
> 所以说, 公钥私钥pair的作用就是 可以push github账号中自己的仓库或是其他协同合作的仓库.而没有权限去push别的账号的仓库
>
> 同时呢,  在网上看到, 一个 git 是可以配置两个github账号的(也就是添加两个账号的公钥私钥pair), 所以,应该是能够在本地push 两个账号的仓库的



> 显然 git 通过邮箱只是生成了本地的公钥和私钥pair ，如果不在github账号中添加生成的公钥的话，只有本地的pair 完全没用啊，没法和github远程仓库产生联系啊，所以当然也没办法push别人的仓库了，

> 在账号B中, 创建了一个仓库 ,并添加了collaborator为账号A，于是账号A接受了邀请，得到了提示:“you now have push access to the ‘账号B仓库’ ”
>
> ![image-20220416170004169](C:\Users\Ryz\AppData\Roaming\Typora\typora-user-images\image-20220416170004169.png)

----

----



##### 关于 local repository 创建了新的分支，而github上没有该分支，却使用 `git push`命令时的问题

解释了：upstream branch 和 remote ”tracking“ branch		

![image-20220414212439727](C:\Users\Ryz\AppData\Roaming\Typora\typora-user-images\image-20220414212439727.png)



##### git 工作树，暂存区和最近提交状态

工作树是指   应该就是**文件夹目录的当前的状态**吧。

所谓提交（Commit），是指“记录工作树中所有文件的当前状态“



执行 `git diff ` ，查看当前工作树与暂存区的差别， 例如： 我修改了一个文件，没有 git add，使用git diff ，就会显示修改的差别。

但如果git add了修改的文件， git diff 不会显示任何内容。



执行 `git diff HEAD` , 查看工作树与最新提交的差别，请执行以下命令。



---

---

##### remote & upstream

还是不太懂啊

比如我用了  `git remote add origin “github地址”` 后，使用 `git branch -a`查看也只是还有本地分支，但是使用 `git remote -v` 却可以查看

到名字叫 origin 的远端仓库他的地址就是我github仓库的地址。

使用 `git push -u(git提示的是--set-upstream) origin "local 分支名"` 再用 `git branch -a`查看才有了  remotes/origin/xxx的分支



如果说github仓库代表的是upstream ，那么remote又被谁指代呢（看不见摸不着的。。）

同时，我push的是 与 github仓库中不同名的分支，会在github仓库中创建了一个与local分支同名的分支，而且，`git branch -a`查看到两个远端分支，一个默认的main， 一个新创建的 local 同名分支，  而当我在github 中的main分支删除，  `git branch -a` 显示的还是这俩分支。

还是要看下这个  [docs](https://devconnected.com/how-to-set-upstream-branch-on-git/)
