# GIT 心得

```
 .-.;;;;;;'                         .;             
(_)  .;                 .-.        .;'             
     :  .;.::..-.  _.;  :  .-.    .;  .-.   .;.::. 
   .:'  .;   ;   :  ;   ;.;.-'   :: .;.-'   .;     
 .-:._.;'    `:::'-'`._.' `:::'_;;_.-`:::'.;'      
(_/  `-        
```                                    

Here are some common instructions for **Git** at work


#### 前置知识

> * clone---克隆
> * init---初始化
> * add---添加
> * commit---提交
> * push---推送
> * fetch---取
> * merge--合并
> * pull---拉（并合并）
> * checkout---签出
> * branch---分支
> * remote---远程



## 一、初始化

> 前置条件，本地目录还没有建立远程连接

### 1. 在现有的目录中初始化仓库

```
git init
```

### 2. 新建一个文件名为`REDEME.md`的文件

## 二、与远程仓库建立连接

添加一个网址为`https://github.com/guestccc/git-study.git`的**仓库**，命名为`origin`

```
git remote add <远程主机> <远程网址>
git remote add origin https://github.com/guestccc/git-study.git
```

---

查看下现有本地与远程的连接

```
git remote -v
```

结果：

```
origin  https://github.com/guestccc/git-study.git (fetch)
origin  https://github.com/guestccc/git-study.git (push)
```

> 注：一个本地可以连接**多个**远程仓库，但是主机名需要区分开

例如：

```
git remote add origin https://github.com/guestccc/git-study.git

git remote add origin2 https://github.com/guestccc/git-study.git    ---   这个网址可以指向其他的仓库
```

其实就是给每个远程仓库取个名字而已，可以是origin,也可以是其他

## 三、推送提交代码到远程

### 1. 单独添加`REDEME.md`/或者添加所有更改

```
git add REDEME.md

git add .   -----所有
```

### 2. 提交到本地仓库

```
git commit -m "备注"
```

### 3.推送到远程仓库

```
git push <远程主机> <本地分支>:<远程分支>
git push origin master:master
```

如果远程分支和本地分支相同，可以写成

```
git push <远程主机>:<远程和本地同名分支>
git push origin master
```

如果本地与远程有建立追踪关系

```
git push
```

忘记是否有建立追踪关系？查看分支信息

```
git branch -vv
```

## 四、拉取更新

### 第一种方法，先拉取后合并

先把远程所以分支更新拉下来，注意，这对本地的代码没有丝毫影响

```
git fetch
```

再指定分支合并

```
git merge <远程主机> <远程分支>:<本地分支>
git merge origin master:master
```

### 第二种方法，直接取到远程对应分支与本地分支合并

```
git pull <远程主机> <远程分支>:<本地分支>
git pull origin master:master
```

## 六、版本回滚

### 首先得知道看下提交历史

```
git log
```

结果

```c
commit 94c9492cc06f934cd5260dd2642361ac3b4229d4 (HEAD -> master, origin/master)
Author: “ccc <1009078602@qq.com>
Date:   Sat Jan 12 16:31:47 2019 +0800

    5

commit ee385d26b0b124109f9543d5a53981d69fe95759--------------这个就是每个版本的id(版本号)
Author: “ccc <1009078602@qq.com>
Date:   Sat Jan 12 16:31:11 2019 +0800

    4

commit f2991c90cf60701280f4fa2b1722a8310d99cd2b
Author: “ccc <1009078602@qq.com>
Date:   Sat Jan 12 16:27:38 2019 +0800
```

### 接着选一个版本进行回滚

```
git reset --hard f2991c90cf60701280f4fa2b1722a8310d99cd2b
```


### 七、克隆

从远程主机`<origin>`克隆一个版本库

1. https协议

`git clone https://github.com/guestccc/git-study.git`

2. ssh协议

`git clone git@github.com:guestccc/git-study.git`

其他的，就不介绍了

### 八、常用