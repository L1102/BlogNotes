# git命令学习

- **git status**：查看所有修改的文件

​	输出以下几种情况：

1. **Changes to be committed**：表示已经添加到暂存区，但还没有被提交的文件。
2. **Changes not staged for commit**：表示这是在工作目录中被修改的文件，但还没有被添加到暂存区（即未使用`git add`命令添加到暂存区）。
3. **Untracked files**：表示在工作目录中新创建的文件，但是还没有被Git跟踪管理。



- **git如何把本地文件全部同步到远程并覆盖远程**

```bash
# 查看当前关联的远程仓库
git remote -v
# 
```

- **git修改、添加远程仓库的名称**

```bash
# 其中 <old_name> 是原始的远程 origin 名称，<new_name> 是你想要修改成的新的名称
git remote rename <old_name> <new_name>
# 添加远程仓库
git remote add <远程仓库名字> <远程仓库URL>
```

- **git提交文件到远程**

```bash
# 查看当前关联的远程仓库
git remote -v
# 切换分支（分支正确就不用切换）
git checkout master
# 添加到暂存区，这里添加了文件的描述信息，commit提交时就不需要再 -m
git add -m "描述信息" 文件名
# 提交到本地的 master 分支
git commit
# 也可以指定提交哪些文件
git commit <file1> <file2> -m "描述信息"
# 推送到远程master分支
# <remote> 是远程仓库的名称，<branch> 是要提交的分支名称
git push <remote> <branch>
```

- **git删除文件和文件夹**

1. 删除文件夹：

```bash
# 1.递归地删除该文件夹下的所有文件和子文件夹，但保留在本地工作区中
git rm -r --cached folder/
# 2. 提交本次更改并添加一个描述性的提交消息：
git commit -m "Remove folder/"
# 3. 更改推送到远程仓库
git push <remote> <branch>
```

2. 删除指定文件

```bash
# 1. 删除指定文件，但保留在本地工作区中
git rm --cached folder/example.txt
# 2. 提交本次更改并添加一个描述性的提交消息：
git commit -m "Remove folder/"
# 3. 更改推送到远程仓库
git push <remote> <branch>
```



- **windows下git中文显示乱码**

原因是因为git默认在命令行中显示文件路径时会对路径进行引号转义处理

**解决：**

```bash
# 设置全局git目录禁止转义（不推荐）
git config --global core.quotepath false
# 设置当前git目录下禁止转义（推荐）
git config --local core.quotepath false

# 其他下相关编码操作：
# 设置Git GUI工具的默认字符编码为UTF-8。这会确保在Git GUI中正确地显示和处理UTF-8编码的字符
git config --global gui.encoding utf-8
# 设置Git日志输出的字符编码为GBK，以便在GBK编码环境中正确地显示和处理日志信息
git config --global i18n.logoutputencoding gbk
# 设置Git提交信息的字符编码为UTF-8
git config --global i18n.commitencoding utf-8
```



































