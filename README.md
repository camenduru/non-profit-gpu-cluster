🐣 Please follow me for new updates https://twitter.com/camenduru <br />
🔥 Please join our discord server https://discord.gg/k5BwmmvJJU <br />
🥳 Please join my patreon community https://patreon.com/camenduru <br />

## Motivation

### A non-profit GPU cluster that runs open-source paper demos with a UI for free for everyone.

https://twitter.com/camenduru/status/1747802652182737050
![image](https://github.com/camenduru/community-gpu-cluster/assets/54370274/99285477-fb17-44e6-ba5f-fce56902dde0)

- If each person receives 24 hours of compute time every week with a 3090 or A5000 GPU 7 people can use it, with 2xGPU 14 people, with 24xGPU 168 people ...
- Operation cost (electricity): 2xGPU 3090 or A5000 24 Hours ~$2
- End-of-the-year goal: 6 servers with a total of 24 x A5000 or 3090 GPUs.


## First Server Parts

- GPU1: Asus ROG Strix RTX3090 O24G (3-slot 24GB with Liquid Cooler 2-slot)
- GPU2: Asus ROG Strix RTX3090 O24G-W (3-slot 24GB with Liquid Cooler 2-slot)
- Motherboard: Pro WS C621-64L SAGE (4 GPU Support)
- CPU: Intel® Xeon® W-3235 Processor (64 Lane PCIe 3.0) (4 GPU Support)
- CPU Cooler: 4U Active CPU Heat Sink LGA3647 (Narrow)
- Ram: Min 128GB (32GBx4) Max 384GB (32GBx12) DDR4 1rx4 2933MHz or 3200MHz
- SSD: 4TB 6Gb/s
- Power supply: Corsair AX1500i 1500 Watt 80+ Titanium
- Case: Antec P20C-W (E-ATX)

## Budget & Sponsors
- [fictions.ai](https://fictions.ai/) [@thibaudz](https://twitter.com/thibaudz) | https://twitter.com/camenduru/status/1749788882877448451
![image](https://github.com/camenduru/non-profit-gpu-cluster/assets/54370274/41756396-6289-4795-bd06-b1f234bf5d73)
- Chai Prize Grant [@chai_research](https://twitter.com/chai_research) | https://twitter.com/chai_research/status/1702811327323070762
![image](https://github.com/camenduru/community-gpu-cluster/assets/54370274/ecef1797-2d8a-42f1-b8f5-d336a9dc3df3)
- December Sponsor [@adhik_Joshi](https://twitter.com/adhik_Joshi) | https://twitter.com/camenduru/status/1729995264096641233
![image](https://github.com/camenduru/community-gpu-cluster/assets/54370274/6e41805b-01ff-40bb-9dfe-38dd2ac7e572)
- January Sponsor [@adhik_Joshi](https://twitter.com/adhik_Joshi) | https://twitter.com/camenduru/status/1744371512981794865
![image](https://github.com/camenduru/community-gpu-cluster/assets/54370274/4c1aa14c-e8ad-461d-a458-d37f78ad4d2e)
- Patreon Members (2023 + Jan 2024) https://www.patreon.com/camenduru
- Total In $2462.58
- Total Out (Optimistic Prediction) $3418 OR $3418 + 8x32GB RAM $760 = $4178
- $3418 - $2462.58 = $955.42 OR $4178 - $2462.58 = $1715.42 😐

## Updates

### January 27, 2024
✔ Power supply2: Corsair AX1500i 1500 Watt 80+ Titanium $227 <br />
✔ Case2 (Antec P20C-W) $89 <br />

### January 24, 2024
✔ GPU2: Asus ROG Strix RTX3090 O24G-W (3-slot 24GB with Liquid Cooler 2-slot) $790 <br />

### January 23, 2024
✔ 🧿 The non-profit GPU cluster is now running [instantid.github.io](https://instantid.github.io/) 🥳 (operating with an old motherboard and CPU because our new CPU has not arrived yet)

### January 22, 2024
✔ 🧿 The non-profit GPU cluster is now running [photo-maker.github.io](https://photo-maker.github.io/) 🥳 (operating with an old motherboard and CPU because our new CPU has not arrived yet)

### January 20 2024
✔ GPU1: Asus ROG Strix RTX3090 O24G (3-slot 24GB with Liquid Cooler 2-slot) $747 <br />
✔ Power supply1: Corsair AX1500i 1500 Watt 80+ Titanium $249 <br />
✔ CPU Cooler1: 4U Active CPU Heat Sink LGA3647 (Narrow) $78 <br />

### January 19 2024
✔ Motherboard1 (Pro WS C621-64L SAGE) $628 <br />
✔ 1 x 32GB RAM1 (Micron 32GB DDR4-3200 RDIMM 1Rx4 CL22) $95 <br />
✔ Case1 (Antec P20C-W) $89 <br />
![mb_one_ram_case](https://github.com/camenduru/Community-GPU-Cluster/assets/54370274/805fdf46-4fee-46d3-a41b-b827d959e860)

## Setup

### SSH root login
```shell
sudo nano /etc/ssh/sshd_config
PermitRootLogin prohibit-password to PermitRootLogin yes
sudo systemctl restart ssh
sudo passwd
sudo ufw allow ssh
```

### Ubuntu 22.04.3 LTS
```shell
apt update
apt upgrade -y
apt install build-essential software-properties-common zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev -y
apt install wget nvtop python-is-python3 python3-pip aria2 unrar -y
```

### Cuda 12.1.0_530.30.02
```shell
lsmod | grep nouveau
cat <<EOF | sudo tee /etc/modprobe.d/blacklist-nouveau.conf
blacklist nouveau
options nouveau modeset=0
EOF
sudo update-initramfs -u
sudo reboot

wget https://developer.download.nvidia.com/compute/cuda/12.1.0/local_installers/cuda_12.1.0_530.30.02_linux.run
sh cuda_12.1.0_530.30.02_linux.run
nvidia-smi
nano /etc/ld.so.conf
ldconfig

nano .bashrc
ldconfig
nvcc --version
```

### Python 3.10.12
```shell
pip install torch==2.1.0+cu121 torchvision==0.16.0+cu121 torchaudio==2.1.0+cu121 torchtext==0.16.0 torchdata==0.7.0 --extra-index-url https://download.pytorch.org/whl/cu121
pip install notebook
pip show torch notebook
```

### Jupyter
```shell
mkdir /content
nano /etc/systemd/system/jupyter-lab.service
systemctl daemon-reload
systemctl start jupyter-lab
systemctl enable jupyter-lab
systemctl list-unit-files --type=service --state=enabled
pip install pickleshare ipywidgets
```

### Network
```shell
nano /etc/netplan/00-installer-config.yaml
netplan apply

wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
dpkg -i cloudflared-linux-amd64.deb
cloudflared service install TOKEN_HERE
```

### Docker
```shell
https://docs.docker.com/engine/install/ubuntu/
https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html#installing-the-nvidia-container-toolkit
systemctl restart docker
https://github.com/jupyter/docker-stacks

https://github.com/camenduru/docker-stacks-foundation
https://github.com/camenduru/base-notebook
https://quay.io/repository/camenduru/docker-stacks-foundation
https://quay.io/repository/camenduru/base-notebook
docker build -t base-notebook .

Ubuntu 22.04 Python 3.10.11
docker container run -it --rm --gpus all -u root -e GRANT_SUDO=yes -p 1000:7860 quay.io/camenduru/base-notebook:latest
docker container run -it --rm --gpus all -u root -e GRANT_SUDO=yes -p 1000:7860 registry.hf.space/camenduru-base-notebook:latest
docker container run -it --rm --gpus all -u root -e GRANT_SUDO=yes -p 1000:7860 camenduru/base-notebook:latest
docker system prune -a
```

### Other
```shell
tmux ls
tmux a
tmux attach-session -t 0

wget https://openrgb.org/releases/release_0.9/openrgb_0.9_amd64_bookworm_b5f46e3.deb
dpkg -i openrgb_0.9_amd64_bookworm_b5f46e3.deb
apt --fix-broken install
openrgb -m off

find / -type f -exec du -h {} + | sort -rh | head -n 20

git clone https://github.com/aristocratos/btop
cd btop
make
make install PREFIX=/usr
```
