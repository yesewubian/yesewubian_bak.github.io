在git仓库的hooks目录下，创建post-receive文件，文件内容如下
```
#!/bin/sh

#判断是不是远端仓库
IS_BARE=$(git rev-parse --is-bare-repository)
if [ -z "$IS_BARE" ]; then
echo >&2 "fatal: post-receive: IS_NOT_BARE"
exit 1
fi

unset GIT_DIR
DeployPath="/var/www/rep2" #要部署的目录，提前clone好

echo "==============================================="
cd $DeployPath
echo "deploying the test web"

#git stash

#git pull origin master

git fetch --all
git reset --hard origin/master

#gitbook build
#sleep 15

time=`date`
echo "web server pull at webserver at time: $time."
echo "================================================"

```

####注意
git用户对要部署的项目目录有操作权限

关于其它的钩子可查看相关文档