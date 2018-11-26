# Docker自動建立Arangodb的指令

```bash
#!/bin/bash
HOST_IP="$1"
if [ -z "${HOST_IP}" ]; then
echo "Usage: d-run-cluster [host IP]"
else
   docker volume create arangodb1
   docker volume create arangodb2
   docker volume create arangodb3
echo "Coordinator IP = " ${HOST_IP} &&
   docker run -d --name=adb1 --rm -p 8528:8528 -v /var/run/docker.sock:/var/run/docker.sock arangodb/arangodb-starter:0.13.8 --starter.address=${HOST_IP} --docker.image=arangodb:3.3
    docker run -d --name=adb2 --rm -p 8538:8528 -v /var/run/docker.sock:/var/run/docker.sock arangodb/arangodb-starter:0.13.8 --starter.address=${HOST_IP} --starter.join=${HOST_IP} --docker.image=arangodb:3.3
    docker run -d --name=adb3 --rm -p 8548:8528 -v /var/run/docker.sock:/var/run/docker.sock arangodb/arangodb-starter:0.13.8 --starter.address=${HOST_IP} --starter.join=${HOST_IP} --docker.image=arangodb:3.3
fi
```
要注意初始化的時候adb1要使用8528這個port不然其他會無法正常連線
