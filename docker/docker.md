# DOCKER指令
## 重啟服務
    systemctl start docker
## 开机自动启动docker
    systemctl enable docker
## Restart the docker daemon.
    sudo service docker restart
## 使用ubuntu运行一个交互性的shell
## 可以使用CTRL -p+CTRL -q --就像先按CTRL -p 然后CTRL -q
    sudo docker run -i -t ubuntu /bin/bash
## 如果不存在docker群组，添加一个用户群组
    sudo groupadd docker
## Add the connected user "${USER}" to the docker group.
    sudo gpasswd -a ${USER} docker
## 切换当前会话到新 group 或者重启 X 会话
    newgrp - docker
## Run this command to download the latest version of Docker Compose
    sudo curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
## Apply executable permissions to the binary
    sudo chmod +x /usr/local/bin/docker-compose