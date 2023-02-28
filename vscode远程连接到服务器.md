好记性不如烂笔头

新配置的vscode如何连接到远程服务器


首先点击`SSH TARGETS`右侧的配置按钮，进入`C:\Users\name\.ssh\config`进行登录配置
```
# Read more about SSH config files: https://linux.die.net/man/5/ssh_config
Host alias
    HostName hostname
    User user
```
`alias`为你想给远程服务器起的名字
`hostname`为服务器的公网`IP`，虚拟机采用`ifconfig`命令进行查询
`user`表示在该服务器上的用户名，如果是`root`用户，则使用`root`这个用户名。

配置成功后会出现一个远程主机的标志

为了避免每次登录都要验证用户名和密码的麻烦，需要使用`ssh`登录。
在本地机器上使用`ssh-keygen`命令，生成`ssh`登录的公钥和私钥。
找到远程主机根目录下的`.ssh`文件夹（如果没有，用`ssh-keygen`生成一下），通过`vim`配置文件夹下的`authorized-keys`文件，将公钥复制进去

之后就不需要每次都输入密码啦。