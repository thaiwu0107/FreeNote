# Linux指令
## 切换到root用户
su root
## 如果創建一個群组，添加一个用户群组
    sudo groupadd docker
## Add the connected user "${USER}" to the docker group.
    sudo gpasswd -a ${USER} docker
## 查看IO情況
    sudo iotop