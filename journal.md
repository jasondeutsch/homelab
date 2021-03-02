# HOMELAB: THE JOURNAL

## Day 0:

### Starting Equipment List:
* 4x rPI 4 4gb
* D-Link DGS-108 network switch
* Cables
* Some Micro SD cards, various capacity, whatever was on hand
* Ethernet cables.
* [C4 Labs cluser](https://www.amazon.com/gp/product/B0844YSJWB/ref=ppx_yo_dt_b_asin_title_o04_s00?ie=UTF8&th=1)
* [balena for flashing SDs](https://www.balena.io/etcher/)
* [ASUS AX5700 because the router from my ISP offerez zero configuration, this will be relevant later](https://www.amazon.com/gp/product/B08BJHS3X7/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&psc=1)

### Choice of OS
I decided on <strong>Raspberry Pi OS Lite</strong> for the only reason is that it lacked a desktop environment so resources would not be wasted there. 
I plan to administer the cluster through the shell via SSH, GUI not needed.

## Day 1:

Headless Pi:

Static IP:

IP Binding in router

Starting in headlessmode
Add SSH file to boot image
Set IP on each device

Change ssh credentails:

K8s

Kubernetes
```shell
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
echo "$(<kubectl.sha256) kubectl" | sha256sum --check
```
Expecfting `kubec: ok`

`kubectl`
```shell
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

helm
```shell
curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
sudo apt-get install apt-transport-https --yes
echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm
```

~lather ~~rinse~ repeate 
