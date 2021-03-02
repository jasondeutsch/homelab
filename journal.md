# HOMELAB: THE JOURNAL

## Day 0:

Equipment List:
* 3x rPI 4 4gb
* D-Link DGS-108 network switch
* Cables
* Some Micro SD cards, various capacity, whatever was on hand
* Ethernet cables.
* C4 Labs cluser



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
