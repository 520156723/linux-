# curl
- -o 表示将返回输出到文件中
  - 示例 $ curl -o linux.html http://www.linux.com 将结果写到linux.html中
- -m 设置最大传输时间
- -s 不输出任何东西
- -w 获取请求结果，常用于诊断
  - 示例 curl -s -w %{http_code} 获取http响应码

# git

- 回退 git reset --hard 139dcfaa558e3276b30b6b2e5cbbb9c00bbdca96

- 切换分支 git checkout 分支名

- 查看分支 git branch

- 查看包括远程分支 git branch -a    `git branch -a | grep hqd`

- 拷贝当前分支为本地新分支 git checkout -b 本地新分支名

- 推送本地分支到远程分支，如果本地分支没有建立过关联，创建同名远程分支并推送 git push origin feature09240928-145141-hqd

- 建立本地分支跟远程分支的关联，之后可以直接push

- 删除本地分支 git branch -d 分支名

- 删除远程分支git push origin --delete 分支名

- 更改分支名 git branch -m 原名 新

- 合并分支A到当前 git merge A

- 标签 tag
  - 打标签 git tag -a v1.0 -m "message"
  - 显示所有标签 git tag
  - 显示指定标签 git show v1.0
  - 删除标签 git tag -d v1.0
  
- rebase有冲突后解决 
  -  放弃 git rebase --abort
  - 继续git rebase –continue
  
- 暂存不提交

  - 保存

    git stash save "2333"

  - 查看所有stash

    git stash list

  - 应用一个stash

    git stash apply stash@{0}

  - 删除

    - 删除一个

      git stash drop stash@{0}

    - 删除全部

      git stash clear


- 换远程仓库目录

   git remote set-url origin git@codeup.aliyun.com:6128d2e757e7cd986dfae5ab/be-hr/be-hr-cts-api.git
   
- 查看远程仓库地址
   git remote -v
   
-  grep 排除, 排除 a 或 b 或 c 的行

   ```shell
   grep -v  'a\|b\|c'
   ```

   ```
   grep -v 'redis \|lettuce\|Connection' error_2021-12-27_1.log
   ```
   
- git pull 失败
git clean  -d  -fx ""
其中 
x  -----删除忽略文件已经对git来说不识别的文件
d  -----删除未被添加到git的路径中的文件
f  -----强制运行
或者 stash 在pull

# 加压解压
   
- 解压jar包

  Jar -xvf xxx.jar

  - 解压到新目录tmp

    Unzip xxx.jar -d tmp
  
- 解压tar 解压到b目录下

  tar -zxvf a.zip -C /home/web/b

- 压缩 tar 把文件a里的全部压缩为a.tar.gz

  tar -zcvf a.tar.gz  a

- 查看md5

  md5sum 目标文件

- 多级创建目录 mkdir -p 

- 修改默认 linux dash
  dpkg-reconfigure dash 改为no

- 批量查找替换  把a改成b
  sed -i 's/a/b/g' connect_sql.ini

# scp
-  scp wii-0.0.1-SNAPSHOT.jar web@116.62.164.233:/home/web/wii   从 a复制到 b

- 复制整个文件夹 把文件夹static下的都复制到远程的static文件夹下，会覆盖

  scp -r static/*  web@116.62.114.95:/home/web/source/admin-front/dist/static/

  往web下添加了新文件夹py_virtualenv
  scp -r py_virtualenv web@172.16.57.24:/home/web
  
# 端口相关
- 看端口对应的pid
  lsof -i:端口号
- 看pid对应的端口
  sudo lsof -nP | grep LISTEN | grep 端口号
- 查看某ip的 端口是否打开

  `nc -zv 192.168.1.15  22`  查看192.168.1.15的22是否打开
  
# 查看ip
- 查看外网ip
  curl ifconfig.me
- 

# 文件相关
- 从⾼到低依次显示当前目录的⽂件和⽬录⼤⼩
  du -sk * | sort -rn
- 查看文件时间

  stat file1 

  - 修改mtime

    ```shell
    touch -mt 1802241622 file1 
    ```

    　　1802241622 代表：

    　　　　18 ---> 2018年

    　　　　02 ---> 2月

    　　　　24 ---> 24号

    　　　　1622 --->时间16:22
        
- 查看md5

  md5sum 目标文件

- 多级创建目录 mkdir -p 

# 定时脚本
  crontab -e：编辑某个用户的crontab文件内容。如果不指定用户，则表示编辑当前用户的crontab文件

  0 1 * * *  --> 分 时 日 月 星期

# 查找替换
- find / -name "nginx"

- 查找某文件中的目标字符串a并且替换成b  sed -i 's/a/b/g' test.log

- find /home/web/api/tomcat-api/logs -mtime +15  -exec rm -rf {} \;

  $ find . **-mtime +15**

  列出当前目录在 15 天以前有修改过的文件，例如今天是6/16，則7天6/2 以前的檔案都列出

  {} \

  表示替换查找到的结果 
  
  # 查看系统版本
  cat /proc/version
  cat /etc/redhat-release
  
  # if
  if [ -z $JAVA_BIN ]
  [-z string] “string”的长度为零则为真 
  [-n string] or [string] “string”的长度为非零non-zero则为真 
