# Git常用命令

## 修改最近一条git commit的author信息
```bash
git commit --amend --reset-author
```

## 批量修改git commit的author信息
使用以下脚本，替换【原来的邮箱】、【修改后的用户名】、【修改后的邮箱】这三处即可。
```bash
#!/bin/sh

git filter-branch --env-filter '
an="$GIT_AUTHOR_NAME"
am="$GIT_AUTHOR_EMAIL"
cn="$GIT_COMMITTER_NAME"
cm="$GIT_COMMITTER_EMAIL"
if [ "$GIT_COMMITTER_EMAIL" = "原来的邮箱" ]
then
    cn="修改后的用户名"
    cm="修改后的邮箱"
fi
if [ "$GIT_AUTHOR_EMAIL" = "原来的邮箱" ]
then
    an="修改后的用户名"
    am="修改后的邮箱"
fi
    export GIT_AUTHOR_NAME="$an"
    export GIT_AUTHOR_EMAIL="$am"
    export GIT_COMMITTER_NAME="$cn"
    export GIT_COMMITTER_EMAIL="$cm"
'
```

## pull合并两个独立启动仓库的历史
```bash
git pull origin master --allow-unrelated-histories
```