# Linux-cmd
Linux 个人常用命令归档

### Rclone

挂载文件夹
```
rclone mount google: /home/driver/google/ --copy-links --no-gzip-encoding --no-check-certificate --allow-other --allow-non-empty --umask 000 &
```

### Git

批量修改commit用户名
```
#!/bin/sh
git filter-branch --env-filter '
OLD_NAME="fmwalways"
CORRECT_NAME="fomav"
if [ "$GIT_COMMITTER_NAME" = "$OLD_NAME" ]
then
    export GIT_COMMITTER_NAME="$CORRECT_NAME"
fi
if [ "$GIT_AUTHOR_NAME" = "$OLD_NAME" ]
then
    export GIT_AUTHOR_NAME="$CORRECT_NAME"
fi
' --tag-name-filter cat -- --branches --tags
```

批量修改commit邮箱
```
#!/bin/sh
git filter-branch --env-filter '
OLD_EMAIL="mengv@outlook.com"
CORRECT_EMAIL="fomav@foxmail.com"
if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```
