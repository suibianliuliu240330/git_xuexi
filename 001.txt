##### 1. 本地仓库初始化
`git init` 
```bash
[john@jm git_jichu]$ git init
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint: 	git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint: 	git branch -m <name>
hint:
hint: Disable this message with "git config set advice.defaultBranchName false"
Initialized empty Git repository in /home/john/Documents/geren_xuexi/git_xuexi/git_jichu/.git/
```
##### 2. 查看当前本地git仓库状态
`git status`
```bash
[john@jm git_jichu]$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
[john@jm git_jichu]$ 
```
##### 3. 将更改后的文件追踪并提交
`git add 文件名`
将被追踪的文件添加到暂存区。
```bash
[john@jm git_jichu]$ git add 001.txt
[john@jm git_jichu]$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   001.txt
```

`git -m "确认提交"`
将文件提交到仓库中
```bash
[john@jm git_jichu]$ git commit  -m "确认提交"
Author identity unknown

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: empty ident name (for <john@jm.local>) not allowed
[john@jm git_jichu]$ 

[john@jm git_jichu]$ git config --global user.email "suibianliuliu240330@outlook.com"
[john@jm git_jichu]$ git config --global user.name "suibianliuliu240330"
[john@jm git_jichu]$ git commit  -m "确认提交"
[master (root-commit) 4691a71] 确认提交
 1 file changed, 30 insertions(+)
 create mode 100644 001.txt
[john@jm git_jichu]$ git status
On branch master
nothing to commit, working tree clean
```

也可以直接添加并提交
`git commit -a -m "直接追踪并提交" __前提是文件已被追踪__
```bash
<Right>[john@jm git_jichu]$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   001.txt

no changes added to commit (use "git add" and/or "git commit -a")
[john@jm git_jichu]$ git commit -a -m "001更改后，从master上提交"
[master 1b4c74d] 001更改后，从master上提交
 1 file changed, 102 insertions(+)

[john@jm git_jichu]$ git status
On branch master
nothing to commit, working tree clean
```



##### 4. gti log
查看提交日志
```bash
[john@jm git_jichu]$ git log
commit 4691a715c1b545fa33343f3e0098f6cf0ebef4a3 (HEAD -> master)
Author: suibianliuliu240330 <suibianliuliu240330@outlook.com>
Date:   Wed Aug 6 12:11:39 2025 +0800

    确认提交
[john@jm git_jichu]$ 
```
##### 5. 分支的创建与切换
`git branch`
查看分支，目前只有一个分支'master'
`git branch fenzhiB`
创建分支B
`git checkout fenzhiB`
切换到分之B上

也可以在创建分支的同时直接切换到分支上
`git checkout -b fenzhiB`

```bash
[john@jm git_jichu]$ git branch
* master
[john@jm git_jichu]$ git branch fenzhiB
[john@jm git_jichu]$ git branch
  fenzhiB
* master
[john@jm git_jichu]$ git checkout fenzhib
error: pathspec 'fenzhib' did not match any file(s) known to git
[john@jm git_jichu]$ git checkout fenzhiB
Switched to branch 'fenzhiB'
[john@jm git_jichu]$ git branch
* fenzhiB
  master
[john@jm git_jichu]$ 
```
##### 5. 合并
切换到master分支，然后输入git merge fenzhiB命令，将fenzhiB分支合并到master分支.
```bash
[john@jm git_jichu]$ git branch
* fenzhiB
  master
[john@jm git_jichu]$ git checkout master
Switched to branch 'master'
[john@jm git_jichu]$ git branch
  fenzhiB
* master
[john@jm git_jichu]$ git merge fenzhiB
Already up to date.
[john@jm git_jichu]$ git branch
  fenzhiB
* master
```
#### 6. 分支的删除
`git branch -d fenzhiB`
如果没有合并前会不不让删除，需要使用-D,强制删除。

#### 7. 设置tag
```bash
[john@jm git_jichu]$ git branch
* master
[john@jm git_jichu]$ git tag v1.0
[john@jm git_jichu]$ git branch
* master
[john@jm git_jichu]$ git tag
v1.0
[john@jm git_jichu]$ git status 
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   001.txt

no changes added to commit (use "git add" and/or "git commit -a")
[john@jm git_jichu]$ git commit -a -m "提交"
[master 6afc348] 提交
 1 file changed, 24 insertions(+)
[john@jm git_jichu]$ git status
On branch master
nothing to commit, working tree clean
[john@jm git_jichu]$ git tag v1.1
[john@jm git_jichu]$ git tag
v1.0
v1.1

[john@jm git_jichu]$ git checkout v1.0
Note: switching to 'v1.0'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 1b4c74d 001更改后，从master上提交


[john@jm git_jichu]$ git status 
HEAD detached at v1.0
nothing to commit, working tree clean
[john@jm git_jichu]$ git checkout v1.1
Previous HEAD position was 1b4c74d 001更改后，从master上提交
HEAD is now at 6afc348 提交
[john@jm git_jichu]$ git status
HEAD detached at v1.1
nothing to commit, working tree clean
[john@jm git_jichu]$ git checkout v1.0
Previous HEAD position was 6afc348 提交
HEAD is now at 1b4c74d 001更改后，从master上提交
[john@jm git_jichu]$ ls -al
total 20
drwxr-xr-x 3 john john 4096  8月  6 12:34 .
drwxr-xr-x 3 john john 4096  8月  6 11:54 ..
-rw-r--r-- 1 john john 3613  8月  6 12:34 001.txt
-rw-r--r-- 1 john john   29  8月  6 12:25 fenzhiB创建的.txt
drwxr-xr-x 7 john john 4096  8月  6 12:34 .git
[john@jm git_jichu]$ ls -alh
total 20K
drwxr-xr-x 3 john john 4.0K  8月  6 12:34 .
drwxr-xr-x 3 john john 4.0K  8月  6 11:54 ..
-rw-r--r-- 1 john john 3.6K  8月  6 12:34 001.txt
-rw-r--r-- 1 john john   29  8月  6 12:25 fenzhiB创建的.txt
drwxr-xr-x 7 john john 4.0K  8月  6 12:34 .git
[john@jm git_jichu]$ git checkout v1.1
Previous HEAD position was 1b4c74d 001更改后，从master上提交
HEAD is now at 6afc348 提交
[john@jm git_jichu]$ ls -alh
total 24K
drwxr-xr-x 3 john john 4.0K  8月  6 12:34 .
drwxr-xr-x 3 john john 4.0K  8月  6 11:54 ..
-rw-r--r-- 1 john john 4.2K  8月  6 12:34 001.txt
-rw-r--r-- 1 john john   29  8月  6 12:25 fenzhiB创建的.txt
drwxr-xr-x 7 john john 4.0K  8月  6 12:34 .git
[john@jm git_jichu]$ ls -al
total 24
drwxr-xr-x 3 john john 4096  8月  6 12:34 .
drwxr-xr-x 3 john john 4096  8月  6 11:54 ..
-rw-r--r-- 1 john john 4295  8月  6 12:34 001.txt
-rw-r--r-- 1 john john   29  8月  6 12:25 fenzhiB创建的.txt
drwxr-xr-x 7 john john 4096  8月  6 12:34 .git
[john@jm git_jichu]$

```
切换tag后，内容也会随着进行更改。


#### 8. 绑定github
- 创建ssh密钥对
ssh-keygen -t rsa 创建密钥对，将公钥内容复制到github中。
- 测试ssh -T git@github.com
```bash
[john@jm git_jichu]$ ssh -T git@github.com
ssh: connect to host github.com port 22: Connection refused

[john@jm .ssh]$ pwd
/home/john/.ssh
[john@jm .ssh]$ ls -l
total 20
-rw-r--r-- 1 john john   57  8月  6 12:56 config
-rw------- 1 john john 2590  8月  6 12:53 id_rsa
-rw-r--r-- 1 john john  561  8月  6 12:53 id_rsa.pub
-rw------- 1 john john  858  8月  6 12:56 known_hosts
-rw-r--r-- 1 john john  102  8月  6 12:56 known_hosts.old
[john@jm .ssh]$ cat config 
Host github.com
    Hostname ssh.github.com
    Port 443
[john@jm .ssh]$

[john@jm git_jichu]$ ssh -T git@github.com
The authenticity of host '[ssh.github.com]:443 ([20.205.243.160]:443)' can't be established.
ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[ssh.github.com]:443' (ED25519) to the list of known hosts.
Hi suibianliuliu240330! You've successfully authenticated, but GitHub does not provide shell access.
```
