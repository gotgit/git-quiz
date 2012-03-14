测试
====

1. 不能提交，提示提交内容为空。最为合适的处理方式是：_____

   a) 执行 ``git commit --allow-empty`` 提交。
   b) 执行 ``git commit -a`` 提交。
   c) 执行 ``git status`` 命令查看状态，再执行添加命令选择要提交的文件。
   d) 执行 ``git commit -m "message..."`` 提交。

2. 对项目中的文件 ``hello.c`` 的更改不满意，让其还原至原始版本的命令是：_____

   a) git reset -- hello.c
   b) git checkout HEAD -- hello.c
   c) git revert hello.c
   d) git update hello.c

3. 修改的文档 ``meeting.doc`` 尚未提交，因为错误地执行了 ``git reset --hard`` 导致数据丢失。丢失的数据能找回么？

   a) 不能。执行硬重置使工作区文件被覆盖，导致数据丢失无法找回。
   b) 能。可以通过 ``git checkout HEAD@{1} -- meeting.doc`` 找回。
   c) 不能。因为未提交所以无法找回。
   d) 不确定。如果在重置前执行了 ``git add`` 命令将 ``meeting.doc`` 加入了暂存区，则可以在对象库中处于悬空状态的文件中找到。

4. 修补提交导致一个新增的重要文件 ``addressbook.txt`` 丢失，能找回么？什么方法最好？

   a) 能找回。用 ``git checkout HEAD@{1} -- addressbook.txt`` 命令。
   b) 不能找回，因为提交丢失了。
   c) 能找回。用 ``git fsck`` 找到处于悬空状态的对象，其中一个就是 ``addressbook.txt`` 文件。
   d) 能找回。用 ``git checkout HEAD^ -- addressbook.txt`` 命令。

5. 将工作区中修改的文件添加到暂存区（新增文件不添加），以备提交，用什么命令标记最快？

   a) ``git add -A``
   b) ``git add -u``
   b) ``git add -p``
   b) ``git add -i``

6. 我使用和其他人不一样的IDE软件，总是在目录下生成以 ``.xx`` 为后缀的临时文件。如何避免把此类文件添加到版本库中呢？

   a) 向版本库中添加一个 ``.gitignore`` 文件，其中包含一条内容为 ``*.xx`` 的记录。
   b) 在文件 ``.git/info/exclude`` 中添加一条内容为 ``*.xx`` 的记录。
   c) 执行 ``git clean -f`` 删除临时性文件。
   d) 更换另外一款IDE软件。

7. 项目跨平台导致文件中的换行符不一致。其中有 Linux 格式换行符（0A），也有DOS格式换行符（0D 0A）。要如何避免此类情况呢？

   a) 向版本库中添加一个 ``.gitattributes`` 文件，在其中包含一条内容为 ``* text=auto`` 的设置。
   b) 修改 ``/etc/gitattributes`` 文件，在其中包含一条内容为 ``* text=auto`` 的设置。
   c) 执行命令 ``git config --global core.autocrlf true`` 。
   d) 执行命令 ``git config --global core.autocrlf input`` 。

8. 下列对于版本库授权说法正确的是：_____

  a) 可以为分支或路径设置不同的写入权限，但不能设置不同的读取权限。
  b) 除管理员外，版本库的创建者都可以为自己创建的版本库授权。
  c) 只要通过授权后，便不能限制所推送的提交的署名作者，可以是任何人。
  d) 如果没有向版本库的写入权限，就一定没有读取权限。

9. 撤销服务器版本库中ID为 ``a2387`` 的提交，用什么操作？

   a) ``git rebase -i a2387^``
   b) ``git checkout a2387^ -- .`` ，再执行提交。
   c) ``git revert a2387``
   d) ``git reset --hard a2387^``

10. 所有改动的文件都已加入暂存区，若希望将其中的 ``other.py`` 文件下次再提交，如何操作？

    a) ``git rm other.py``
    b) ``git checkout -- other.py``
    c) ``git checkout HEAD other.py``
    d) ``git reset -- other.py``

11. 若产品的版本号显示为 ``1.7.10.rc0-33-g9678d-dirty`` ，可以判断出此版本号是如何生成的么？

    a) ``git describe --tags --always --dirty``
    b) ``git describe``
    c) ``git name-rev HEAD``
    d) ``git --version``

12. 关于 ``git clone`` 下面说法错误的是：_____

    a) 克隆时只有远程版本库HEAD指向的分支被克隆。
    b) 克隆时所有分支均被克隆，但只有HEAD指向的分支被检出。
    c) 可以通过 ``git clone --single-branch`` 命令实现只克隆一个分支。
    d) 克隆出的工作区中执行 ``git log``\ 、\ ``git status``\ 、\ ``git checkout``\ 、\ ``git commit``\ 等操作不会去访问远程版本库。

13. 对于命令 ``git push`` 的默认行为，说法错误的是：____

    a) 当前分支总是会被推送。
    b) 会推送本地和远程共有的分支。
    c) 若远程版本库为空（刚初始化完毕），不带参数地执行 ``git push`` 不会有分支被推送，但也不会报错。
    d) 本地创建的里程碑（tag）不会被推送。

14. 关于删除分支 ``XX`` ，下列说法正确的是：

    a) 执行 ``git branch -D XX`` 删除分支，总是能成功。
    b) 执行 ``git push origin :XX`` 来删除远程版本库的 ``XX`` 分支。
    c) 远程版本库删除的分支，在执行 ``git fetch`` 时本地分支自动删除。
    d) 本地删除的分支，执行 ``git push`` 时，远程分支亦自动删除。

15. 下面的操作中哪一个不能确认维护分支 ``maint`` 上所有的 bugfix 提交均已合并至当前分支 ``master`` 中。

    a) ``git rev-list ..maint`` 的输出为空。
    b) ``git log ..maint`` 的输出为空。
    c) 新版本发布，在 ``maint`` 分支执行 ``git merge --ff-only master`` 成功。
    d) 在 ``maint`` 分支成功地执行 ``git merge master``\ 。

16. 一个图片文件 ``logo.png`` 冲突了，如何取出他人的版本。

    a) ``git show :0:./logo.png``
    b) ``git show :1:./logo.png``
    c) ``git show :2:./logo.png``
    d) ``git show :3:./logo.png``

17. 关于Git提交说明，错误的说法是：_____

    a) Git提交说明建议采用“50/72原则”。其中提交说明的第一行会作为邮件标题、软件变更记录中的摘要，不宜太长。
    b) 在提交说明中加入 ``Signed-off-by: User <email>`` 的目的是为了避免修补提交导致原始作者跟踪不到，并且方便对所有该提交的贡献者进行追踪。
    c) 提交说明中若出现非 ASCII字符（如中文）且平台内码非 UTF-8 时，需要设置 ``i18n.commitEncoding`` 配置变量以便在跨平台时提交说明不会出现乱码。
    d) 没人关心提交说明，所以提交说明写得比提交内容还多是浪费时间。

18. 发现Bug出现在文件 ``time.c`` 第50行，使用下面的哪条命令可以迅速定位是谁在哪个提交引发的Bug？
    
