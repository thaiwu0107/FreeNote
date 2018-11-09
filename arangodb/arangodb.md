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
   docker run -d --name=adb1 --rm -p 8528:8528 -v arangodb1:/data -v /var/run/docker.sock:/var/run/docker.sock arangodb/arangodb-starter --starter.address=${HOST_IP} &&
   docker run -d --name=adb2 --rm -p 8538:8528 -v arangodb1:/data -v /var/run/docker.sock:/var/run/docker.sock arangodb/arangodb-starter:latest --starter.address=${HOST_IP} --starter.join=${HOST_IP} &&
   docker run -d --name=adb3 --rm -p 8548:8528 -v arangodb1:/data -v /var/run/docker.sock:/var/run/docker.sock arangodb/arangodb-starter:latest --starter.address=${HOST_IP} --starter.join=${HOST_IP}
fi
```
