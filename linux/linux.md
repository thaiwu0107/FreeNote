# Linux指令
## 切换到root用户
su root
## 如果創建一個群组，添加一个用户群组
    sudo groupadd docker
## Add the connected user "${USER}" to the docker group.
    sudo gpasswd -a ${USER} docker
## 查看IO情況
    sudo iotop
## port 佔用 殺掉8000
    sudo lsof -t -i tcp:8000 | xargs kill -9
## 查看 5432
    lsof -i tcp:5432
## 查看 硬碟空間資訊
```
df -h 可知道目前硬碟剩餘空間與使用空間

du -h 可知目前此資料夾下所有檔案與資料夾所佔硬碟大小總數

du -s 可知目前此資料夾總共佔用硬碟大小總數，以G為單位

du -sh 可知目前此資料夾總共佔用硬碟大小總數，以G為單位

ls -l可看檔案大小
```