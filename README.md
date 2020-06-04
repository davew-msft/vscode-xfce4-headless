

based off of:  
https://github.com/swined/super-couscous/blob/master/Dockerfile
and 
https://github.com/danielguerra69/ubuntu-xrdp

```bash

cd documentation/proxmox/docker-xfce4-headless/

ssh root@pve07.davewentzel.local
mkdir -p /dave/pve07SSD02/docker/xfce4
cd /dave/pve07SSD02/docker/xfce4
nano dockerfile
mkdir -p installers
cd installers
nano chromium.sh
nano entrypoint.sh
nano supervisor.conf
nano supervisord.conf
nano tools.sh
nano user-dave.sh
nano xfce-configure.sh
nano xfce_startup.sh

cd ..

docker stop xfce4
docker rm xfce4
docker image rm davew/xfce4

docker build -t davew/xfce4 .  --label "version=0.1"

docker run --name xfce4 \
    --restart always \
    -d \
    -p 2022:22 \
    -p 3389:3389 \
    --privileged \
    -v /plexmnt2:/plexmnt2 \
    davew/xfce4

docker ps

docker exec -it xfce4 /bin/bash





ssh root@127.0.0.1 -p25
ssh dave@127.0.0.1 -p25
```

guac needs to be:  
proxy enc none
sec mode tls enc
check ignore svr cert

google-chrome --no-sandbox --disable-dev-shm-usage
