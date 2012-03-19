Git练习题（B）
===============

单项选择题
-----------

1. 如果刚刚完成的提交说明写错了，应该如何操作？ _____

   a) 执行 ``git commit -m "message..."`` 重写提交说明。
   b) 执行 ``git reset --hard HEAD^`` ，丢弃最新提交。
   c) 执行 ``git revert HEAD`` 反转最新提交。
   d) 执行 ``git commit --amend`` 进行修补提交。

2. 如果项目中文件 ``Hello.java`` 被不小心从工作区删除了，下面哪个命令可以找回该文件？ _____

   a) ``git revert Hello.java``
   b) ``git update Hello.java``
   c) ``git checkout HEAD -- Hello.java``
   d) ``git reset -- Hello.java``

3. 修补提交导致之前提交中的文件 ``addressbook.txt`` 的重要数据丢失，能找回么？什么方法最好？ _____

   a) 不能找回，因为提交丢失了。
   b) 能找回。用 ``git checkout HEAD@{1} -- addressbook.txt`` 命令。
   c) 能找回。用 ``git fsck`` 找到处于悬空状态的对象，其中一个就是 ``addressbook.txt`` 文件。
   d) 能找回。用 ``git checkout HEAD^ -- addressbook.txt`` 命令。

4. 将工作区中所有文件添加到暂存区（忽略文件除外），以备提交，用什么命令标记最快？ _____

   a) ``git add -A``
   b) ``git add -u``
   c) ``git add -p``
   d) ``git add -i``

5. 下面哪一个命令会改变提交历史？ _____

   a) ``git revert HEAD^^``
   b) ``git reset --hard HEAD``
   c) ``git rebase -i HEAD^^``
   d) ``git cherry-pick a32c67d``

6. 向版本库中添加一个 ``.gitignore`` 文件，其中包含 ``*.txt`` 的内容。若版本库中已有文件 ``README.txt`` 。则下列说法正确的是： _____

   a) 文件 ``README.txt`` 被删除。
   b) 文件 ``README.txt`` 不受忽略文件 ``.gitignore`` 的影响，修改状态会被追踪。
   c) 文件 ``README.txt`` 会显示合并冲突。
   d) 对文件 ``README.txt`` 的任何更改将被忽略。
   
7. 项目跨平台会因为文件名是否区分大小写，导致文件冲突。下面说法正确的是： _____

   a) 在大小写敏感的Linux系统上设置配置变量 ``core.ignorecase`` 值为 ``true`` 。
   b) 在大小写不敏感的Linux系统上设置配置变量 ``core.ignorecase`` 值为 ``false`` 。
   c) 在大小写不敏感的Windows系统上设置配置变量 ``core.ignorecase`` 值为 ``true`` 。
   d) 在大小写不敏感的Windows系统上设置配置变量 ``core.ignorecase`` 值为 ``false`` 。

8. 下列对于版本库授权说法正确的是：_____

   a) 只要通过授权后，便不能限制所推送的提交的署名作者，可以是任何人。
   b) 除管理员外，版本库的创建者都可以为自己创建的版本库授权。
   c) 如果没有向版本库的写入权限，就一定没有读取权限。
   d) 可以为分支或路径设置不同的写入权限，但不能设置不同的读取权限。

9. 发现最新提交有错误，如果该提交已经被推送至远程服务器，如何在不改变历史的情况下撤销错误的提交？ _____

   a) ``git rebase -i HEAD^ ; git push -f``
   b) ``git revert HEAD ; git push``
   c) ``git checkout HEAD^ -- . ; git push``
   d) ``git reset --hard HEAD^ ; git push -f``

10. 从版本库中的历史提交中彻底移除倒数第二个（前一个）提交，？ _____

    a) ``git rebase --onto HEAD^^ HEAD^ HEAD``
    b) ``git reset --hard HEAD^^``
    c) ``git checkout HEAD^^ -- .``
    d) ``git revert HEAD^``

11. 所有改动的文件都已加入暂存区，若希望将其中的 ``other.py`` 文件下次再提交，如何操作？ _____

    a) ``git rm --cached other.py``
    b) ``git checkout -- other.py``
    c) ``git revert -- other.py``
    d) ``git reset -- other.py``

12. 若产品的版本号显示为 ``1.7.10.rc0-33-g9678d`` ，可以判断出此版本号是如何生成的么？ _____

    a) ``git log -1 --stat HEAD``
    b) ``git name-rev HEAD``
    c) ``git describe``
    d) ``git --version``

13. 对于命令 ``git push`` 的默认行为，说法\ **错误**\ 的是：____

    a) 当前分支总是会被推送。
    b) 会推送本地和远程共有的分支。
    c) 若远程版本库为空（刚初始化完毕），不带参数地执行 ``git push`` 不会有分支被推送。
    d) 本地创建的里程碑（tag）不会被推送。

14. 关于删除远程分支 ``XX`` ，下列说法正确的是： _____

    a) 执行 ``git branch -D XX`` 删除远程版本库的 ``XX`` 分支。
    b) 执行 ``git push origin :`` 来删除远程分支。
    c) 远程版本库删除的分支，在执行 ``git fetch`` 时本地分支自动删除。
    d) 执行 ``git push origin :XX`` 来删除远程分支。

15. 关于Git提交说明，错误的说法是：_____

    a) Git提交说明建议采用“50/72原则”。其中提交说明的第一行会作为邮件标题、软件变更记录中的摘要，不宜太长。
    b) 在提交说明中加入 ``Signed-off-by: User <email>`` 的目的是为了避免修补提交导致原始作者跟踪不到，并且方便对所有该提交的贡献者进行追踪。
    c) 没人关心提交说明，所以提交说明写得比提交内容还多是浪费时间。
    d) 提交说明中若出现非 ASCII字符（如中文）且平台内码非 UTF-8 时，需要设置 ``i18n.commitEncoding`` 配置变量以便在跨平台时提交说明不会出现乱码。

16. 一个图片文件 ``logo.png`` 冲突了，如何取出我们的版本。 _____

    a) ``git show :1:./logo.png > logo.png-mine``
    b) ``git show :2:./logo.png > logo.png-mine``
    c) ``git show :3:./logo.png > logo.png-mine``
    d) ``git show :0:./logo.png > logo.png-mine``

17. 发现Bug出现在文件 ``time.c`` 第50行，使用下面的哪条命令可以迅速定位是谁在哪个提交引发的Bug？ _____
   
    a) ``git log -p time.c``
    b) ``git diff --stat HEAD^ -- time.c``
    c) ``git bisect start``
    d) ``git blame -L50,+1 time.c``

18. 完成特性开发，请求项目管理者审核，如何更好地将创建变更日志以通知管理者？ _____

    a) ``git log origin/master..``
    b) ``git diff-tree origin/master..``
    c) ``git request-pull origin/master URL-of-your-repo``
    d) ``git diff --stat origin/master``

19. 操作HTTPS协议的版本库时报告证书错误，无法继续操作。下面的操作中那个\ **无效**\ ？ _____

    a) 执行 ``git config --global http.sslVerify false`` 。
    b) 执行 ``git config --global core.autocrlf input`` 。
    c) 执行 ``export GIT_SSL_NO_VERIFY=true`` 。
    d) 换用 SSH 或者 HTTP 协议。

20. 当一个提交说明显示为 ``souce code refactor (see #529)`` ，下面哪个说法是正确的？ _____

    a) 这个提交和项目的缺陷跟踪平台（如Redmine）关联。
    b) 这个提交和项目的缺陷跟踪平台（如Redmine）关联，并会更新相关问题的状态。
    c) 这个提交修正了第529号提交，没有改变版本库的提交历史。
    d) 这个提交撤销了第529号提交，改变了版本库的提交历史。

..
   19. 显示工作区中哪些文件被忽略，可用命令：_____
   
       a) ``git status -s``
       b) ``git status --ignored -s``
       c) ``git stauts -v``
       d) ``git clean -n``
   
   20. 关于 ``git diff`` 命令错误的说法是：_____
   
       a) ``git diff`` 可以在版本库之外执行，就像 GNU diff 命令一样操作，而且提供对二进制文件的支持。
       b) ``git diff --binary`` 提供对二进制文件的支持。
       c) ``git diff`` 格式的补丁文件需要使用 ``git apply`` 命令应用。
       d) ``git diff`` 命令无输出，说明提交列表为空，无需提交。
   
   
