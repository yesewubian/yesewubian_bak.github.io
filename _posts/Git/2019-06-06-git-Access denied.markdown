用户名或密码修改后，执行 git pull 等命令会出现问题 remote: HTTP Basic: Access denied，需要使用新的密码来操作，但是又没有给出输入用户名和密码的提示，

执行命令 `git config --system --unset credential.helper` 命令，作用就是清空本地保存的用户名和密码.使用后发现每次操作远程仓库都需要重新输入用户名和密码，原因是git config --system --unset credential.helper这个命令清空gitconfig里的自动保存用户名和密码配置

执行命令 `git config --global credential.helper store`

这样你只需要再输入一次用户名和密码，系统就会自动保存你的用户名和密码。