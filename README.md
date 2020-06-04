

```bash

docker build -t davew/xfce4 .  --label "version=0.1"

docker run --name xfce4 \
    --restart always \
    -d \
    -p 2022:22 \
    -p 3389:3389 \
    --privileged \
    davew/xfce4

docker ps

docker exec -it xfce4 /bin/bash

ssh root@127.0.0.1 -p25
ssh dave@127.0.0.1 -p25
```

now you can connect with rdp to localhost:3389

to start chrome you have to:  
google-chrome --no-sandbox --disable-dev-shm-usage

