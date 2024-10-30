CLOUDFLARED_TAG 
CLOUDFLARED_SECRET
CLOUDFLARED_ID 
CLOUDFLARED_HOSTNAME

CODE_SERVER_PASSWORD

apt install speedtest-cli
speedtest

apt install sysbench
sysbench cpu --cpu-max-prime=20000 run

- cloudflared service install token_here
- tmux
- mongod --dbpath /var/lib/mongodb
- cd /content
- git clone https://github.com/camenduru/web2
- cd /content/web2
- ./mvnw -Pprod clean package
- cd /content
- git clone https://github.com/camenduru/dispatcher2
- git clone https://github.com/camenduru/scheduler2
- cd /content/scheduler2
- ./mvnw clean package