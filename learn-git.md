
# Git管理仓库基本指令

## git -v:
用于显示当前安装的 Git 版本,-v 选项代表“verbose”
## 使用git config命令配置用户名：
git config --global user.name "XXX"  :(因为有空格，所有用双引号括起来，无空格可省略)  
省略(Local):本地配置，只对本地仓库有效   
--global:全局配置，所有仓库生效   使用最多   
--system:系统配置，对所有用户生效  一般不使用
## 使用git config命令配置邮箱：
git config --global user.email XXX@gmail.com

**这两个命令只需要执行一次！**
## 保存用户名和密码：
git config --global credential.helper store
## 查看git配置信息：
git config --global --list

**配置完成之后就可以使用git来管理我们的代码了！**

## mkdir 创建新目录（文件夹）:
mkdir learn-git
## cd切换目录：
cd learn-git
## git init
用于初始化一个新的 Git 仓库。运行 git init 命令时，Git 会在当前目录中创建一个新的 .git 目录，这个目录包含了所有必要的 Git 仓库文件，以便你可以开始版本控制你的项目。
## git init my-repo
这将在当前目录下创建一个名为 my-repo 的新目录，并在该目录中初始化一个新的 Git 仓库。
## ls
用于列出目录内容。
+ ls -a 列出所有文件，包括隐藏文件（以点开头的文件）。
+ ls -l 以长格式列出信息，包括文件权限、所有者、大小等
+ ls -t 按修改时间排序，而不是默认的字母顺序。
+ ls -r 反向或递归列出文件。
## echo
用于创建文件。
+ echo "内容" > 文件名.txt  
将 "内容" 写入到名为 文件名.txt 的文件中,若文件不存在，会被创建；若已存在，内容会被覆盖。
+ echo "追加内容" >> 文件名.txt  
"追加内容" 会被添加到 文件名.txt 的末尾。
## cat
用于显示文件内容，合并文件以及创建新文件.
+ cat 文件名.txt   
将 文件名.txt 的内容输出到终端
+ cat 文件1.txt 文件2.txt > 合并文件.txt   
将 文件1.txt 和 文件2.txt 的内容合并，并保存到 合并文件.txt 中。
+ cat > 新文件.txt   
输入内容后，按 Ctrl + D（Linux/Mac）或 Ctrl + Z（Windows）结束输入，这样会创建一个新文件并写入你输入的内容。
## git status
查看仓库状态。  
用于显示当前工作目录的状态。(当前分支的状态，上次提交以来，哪些文件被修改了，哪些文件目前处于暂存状态，哪些文件自上次提交以来被删除了，哪些文件目前未被跟踪)
## git add
添加到暂存区。  
+ git add 文件名.txt   
用于将文件的更改添加到暂存区（staging area），这是准备下一次提交（commit）的第一步。
+ git add 文件名1.txt 文件名2.txt   
将多个指定文件添加到暂存区。
+ git add .   
添加所有修改过的文件
+ git add *.txt   
将当前目录下所有.txt文件的更改添加到暂存区。这里的 *.txt 是一个通配符，表示匹配当前目录下所有扩展名为 .txt 的文件。
## git ls-files
用于列出所有 Git 追踪的文件或特定状态下的文件（例如未被追踪的文件、被忽略的文件等），不显示内容上的差异。  包括工作区中未被修改的文件，工作区已修改但未暂存文件和已暂存但未提交的文件。
## git commit
提交。  文件只有被提交到仓库中，才算真正被保管起来。
+ git commit -m "第一次提交"  
使用-m选项后跟提交信息，将暂存区的所有更改提交到本地仓库。
+ git commit -a -m "第一次提交"  或者  git commit -am "第一次提交"   
  -a：这个参数告诉 Git 自动将所有已修改（tracked）的文件添加到暂存区（staging area），然后进行提交。这意味着你不需要先使用 git add 命令来添加文件。 

若不想在命令行中输入提交信息，可以使用： git commit   
这将打开默认文本编辑器，让你写提交信息。
## git log
提供关于项目历史的各种信息，包括提交的元数据、作者、日期和提交信息。
+ git log --oneline   
查看简洁的提交记录,每个提交前面都有一个简短的哈希值。
## cp -rf 源目录名称 目标目录名称
cp 用于复制文件和目录;  
-r 告诉 cp 命令递归地复制整个目录，包括所有子目录和文件;   
-f 用于强制复制，它会在复制前删除目标目录中已存在的同名文件，而不提示任何确认。
## git reset --soft commit-hash
将当前分支的 HEAD 指针移动到指定的提交。  
--soft 选项会保留暂存区的更改，即撤销的提交内容仍然会保留在暂存区中（暂存区）。不改变工作目录，即撤销的提交的更改仍然保留在工作目录中（工作区）。  
commit-hash是git log --online运行后每个提交前面的简短的哈希值。
## git reset --hard HEAD^
将当前分支的HEAD指针回退到当前分支的上一个提交，并清除自那次提交以来的所有更改。   
HEAD: 表示当前分支的最新提交节点。   
HEAD^: 表示当前提交的父提交，即上一个提交。
## git reset HEAD^              
不使用任何选项的git reset命令,默认就是mixed模式;  
(mixed)  
暂存区会被更新，撤销的提交的更改会被取消暂存。工作目录不受影响，即撤销的提交的更改仍然保留在工作目录中。

**git中的所有操作都是可以回溯的；**
## git reflog
显示了 HEAD 或其他引用的更新历史。这个历史包括了所有的操作，比如提交（commit）、重置（reset）、切换分支（checkout）等，即使这些操作使得某些提交不再可达;  

git reflog 的一个常见用途是当你不小心用 git reset --hard 重置了 HEAD，丢失了一些提交，你可以通过查看 reflog 来找回这些丢失的提交的哈希值;

git reflog也可以用来查看已经删除的分支的最后提交点，从而恢复分支/。   
git reset --hard commit-hash   恢复到那个提交
## git diff
用于显示文件或目录的内容差异。这些差异可以是未暂存的更改、不同提交之间的差异，或者是分支之间的差异。
+ git diff  
将显示当前工作区与暂存区之间的差异。
+ git diff HEAD  
比较工作区与版本库之间的差异。
+ git diff --cached / git diff --staged  
比较暂存区与版本库之间的差异。  
用于比较 暂存区 和 最后一次提交 之间的差异，显示哪些文件的内容已经被修改和暂存，但尚未提交。
+ git diff <commit1> <commit2>  
后面加上两次版本的提交ID就可以比较这两个版本之间的差异。
+ git diff <commit1> HEAD
+ git diff HEAD~(^) HEAD
+ git diff HEAD~2 HEAD~3  
  HEAD~表示最新提交的上一次提交，HEAD~2表示最新提交的前两次提交。
+ git diff  <branch_name> <branch_name>  
比较两个分支之间的差异。
## vi filename.txt
vi 是一个流行的文本编辑器，它有两种模式：命令模式和插入模式。
## git rm
+ rm file1.txt   
命令 rm file1.txt 在 Unix-like 操作系统中用于删除名为 file1.txt 的文件。  
(这是删除工作区的文件，暂存区还没有删除，需要用git add file1.txt或者git add .来更新暂存区的内容)
+ git rm file.txt   
删除文件并从暂存区中移除.
+ git rm --cached file1.txt   
只从本地仓库和暂存区中删除文件，不删除工作目录中的文件.
+ git rm -f file1.txt   
强制删除文件
+ git rm -r*  
  递归删除某个目录下的所有子目录和文件

**删除后不要忘记提交git commit -m"XXXX"   !**
## .gitignore
.gitignore 文件是一个由你创建的文件，用来告诉 Git 忽略特定的未跟踪文件和目录，不让这些文件被加入到 Git 的跟踪中。这通常用于排除操作系统生成的文件、编译生成的文件、配置文件等，这些文件通常不需要加入版本控制。
+ echo access.log > .gitignore  
  将access.log日志文件添加到.gitignore文件中
+ vi .gitignore  
  可以编辑修改.gitignore文件  
```vim
# 忽略所有 .log 文件
*.log
# 忽略所有在 temp 目录下的文件和目录
temp/
```
以上修改好.gitignore后，echo hello > hello.log 创建log文件后  
使用git status查看仓库状态，只能看到.gitignore文件被修改，hello.log文件的修改被忽略了；  
git commit -am "test ignore log"    
(-a:自动将所有已暂存的文件（包括新文件）包含到提交中)  
使用git ls-files查看追踪文件时，可以看到hello.log文件没有被添加进来

## 生成SSH Key:
+ ssh-keygen -t rsa -b 4096  
用于生成SSH密钥
+ 私钥文件:id_rsa
+ 公钥文件:id_rsa.pub
## 克隆远程仓库
+ 克隆仓库：git clone repo-address
+ 推送更新内容: git push remote branch  
remote：远程仓库的名称。默认情况下，远程仓库的名称是 origin，但你也可以将其命名为其他名称，如 upstream、origin、heroku 等。   
branch：你想要推送的本地分支的名称。
+ 拉取更新内容: git pull remote   
Git 会从指定的远程仓库 remote 拉取数据，并尝试将拉取的内容与当前检出的本地分支合并。
## 关联本地仓库和远程仓库
### git remote add <shortname><url>
添加一个远程仓库，将一个新的远程仓库连接到本地git仓库  
例如：git remote add origin https://github.com/user/repo.git  
origin 是远程仓库的简写名称，https://github.com/user/repo.git 是远程仓库的URL。
## git remote -v
查看当前仓库所对应的远程仓库的简写别名和地址，会列出所有已配置的远程仓库及其对应的URL。
## git branch -M new-branch-name
用于将当前分支重命名为 new-branch-name；它是一个更简洁和安全的方式来重命名当前检出的分支。  
-M：这是一个选项，用于强制重命名当前分支，即使远程分支已经存在具有相同名称的分支。
## git push
用于将本地仓库的更改上传到远程仓库。

+ git push origin main  
推送当前分支到名为 origin 的远程仓库
+ git push -u origin master:main  
  用于将本地的 master 分支推送到远程仓库的 main 分支，并设置 origin 为该分支的上游（tracking）远程仓库。
## git pull
+ git pull  
  自动拉取远程仓库origin 上的 main 分支的更新
+ git pull <远程仓库名><远程分支名>:<本地分支名>  
  把远程仓库的指定分支拉取到本地再进行合并
## git branch
+ git branch  
  查看当前仓库的所有分支（本地）,并用星号 (*) 标记当前分支。  
  git branch -r 列出所有远程分支  
  git branch -a  查看所有分支（本地和远程）
+ git branch new-branch-name  
  创建一个新的分支，名称为 new-branch-name。
+ git checkout branch-name  
  切换到branch-name分支,将工作目录和暂存区更新到指定分支的状态。
+ git switch branch-name  
  切换到branch-name分支

**分支合并之后，如果不手动删除这个分支的话，它还是会存在的。**
+ git branch -d dev  
  删除已合并的名为dev的分支；但是如果没有被合并的话，是不能用-d参数删除的
+ git branch -D branch-name  
  即使branch-name分支没有被合并，可以用-D参数来强制删除这个分支；
+ git log --graph --oneline --decorate --all  
  查看分支图
## git merge dev
将名为 dev 的分支合并到当前分支。这里的 "当前分支" 是指你执行命令时所在的分支。合并操作会将 dev 分支的历史记录合并到你当前所在的分支中。
## 解决合并冲突
git merge合并后 冲突了之后； vi file.txt 进入文件夹在vim中修改最终的内容，然后进行添加暂存，提交就可以了；
也可以先用 git merge --abort 来中断当前的冲突合并操作；
## ssh -T git@github.com
测试 SSH 连接：运行以下命令，测试你的 SSH 密钥是否能够正确连接到 GitHub：
## ssh-add xxxxx.ssh/id_rsa
添加私钥