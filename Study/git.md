sqm:
	/home/sqm/repositories/github.git
	git init
	touch newfiles
	git add newfiles
	git commit -m "---"
		or	git commit -a -m "---"
	git remote add origin https://github.com/sqm2050/-juson.git

[alias]
	co = checkout
	ci = commit
	st = status
	br = bran


git:从sqm clone 然后更改远程仓库连接，更内容、提交、push。
	git clone sqm@localhost:repositories/github.git		/*这里一定是用户home目录的相对路径*/

	git remote -v
		origin	sqm@localhost:repositories/github.git (fetch)
		origin	sqm@localhost:repositories/github.git (push)

	git remote set-url origin sqm@localhost:repositories/github.git	/*更改远程地址*/

	view readme.txt
		/******
		Here ,added by user git
 		*****/
	git commit -a
	git push

sqm:sqm pull，显示有新的变更了。
	git pull
	From https://github.com/sqm2050/-juson
    3e2ef3f..f849af0  master     -> origin/master
	Updating 3e2ef3f..f849af0
	Fast-forward
	readme.txt |    4 ++++
	1 file changed, 4 insertions(+)

git:创建新的分支，并且同时把sqm的地址也加到origin，把新建的分支push到远程仓库
	git branch b1
	view readme.txt

/******
Here ,added by user git in branch b1 !
 *****/
	git remote set-url --add origin  sqm@localhost:repositories/github.git
	/*添加其他的远程标识。git clone过来的名字默认是origin 可以更改的git remote*/
	git remote add orisqm sqm@localhost:repositories/github.git
	
	git push origin b1 		/*这里带上新的分支，就会把新的分支加入到远程仓库*/
git push:
    refusing to update checked out branch: refs/heads/master	拒绝更新检出的分支（默认）
    By default, updating the current branch in a non-bare repository     在一个non-bare仓库更当前分支是不可以的
    is denied, because it will make the index and work tree inconsistent	因为它将使得索引和工作数与你push的不一致
    with what you pushed, and will require 'git reset --hard' to match	需要"git reset --hard"把work tree匹配到头指针。
    the work tree to HEAD.
    
    You can set 'receive.denyCurrentBranch' configuration variable to	
    'ignore' or 'warn' in the remote repository to allow pushing into
    its current branch; however, this is not recommended unless you
    arranged to update its work tree to match what you pushed in some
    other way.
    
    To squelch this message and still keep the default behaviour, set
    'receive.denyCurrentBranch' configuration variable to 'refuse'.
    可以直接修改文件：
    	--system	/etc/gitconfig
    	--global	~/.gitconfig
    	--local		.git/config
    也可以用：git config
    	git config --global user.name sqm2050	/--注意不要等号--/

## 忽略已经跟踪的文件/目录
```
	git rm --cached ufile/udir
```
## 远程分支
### 检出远程分支
```
	git checkout -b master origin/master
	或者
	git checkout -t origin/master
```
### 创建按本地分支
```
	git branch 分支名
```

### 本地分支复制到远程
```
	git push origin 分支名
```

### 提交分支数据到远程服务器
```
	git push origin 本地分支名:分支名
```

### 删除远程分支 - tag
```
	git push origin :分支名
		or
	git push origin --delete <branchName>
	
	git push origin -d <tagName>
		or
	git push origin --delete tag <tagName>
```

### 获取远程tag
```
	git fetch origin tag <tagName>
```

## 本地复制
复制一个分支:
```
	git clone -b 分支名 本地仓库目录 复制的目的目录
```

### 删除被gitignore忽略的文件
```
git ignore -xdf
```
x 选项忽略.gitignore文件的规则，而是根据-e来忽略。
