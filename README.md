# HOMELAB: THE JOURNAL

![yup](1point21.png)

## Day 0: Shopping list

### Starting Equipment List:
* 4x rPI 4 4gb
* HP EliteDesk 800 G2 Mini
* D-Link DGS-108 network switch
* Cables
* Some Micro SD cards, various capacity, whatever was on hand
* Ethernet cables.
* [C4 Labs cluser](https://www.amazon.com/gp/product/B0844YSJWB/ref=ppx_yo_dt_b_asin_title_o04_s00?ie=UTF8&th=1)
* [balena for flashing SDs](https://www.balena.io/etcher/)
* [ASUS AX5700 because the router from my ISP offerez zero configuration, this will be relevant later](https://www.amazon.com/gp/product/B08BJHS3X7/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&psc=1)

### Choice of OS
All nodes will be headless installs. The Pis will recieve [Ubuntu for Raspberry Pi](https://ubuntu.com/raspberry-pi) and the G2 Mini will get Ubuntu Server.

## Day 1: Connecting the bits and bops

### Headless Install:

We setup SSH to be on by default in our OS image. Once we locate the IP of this device we can simply ssh into it.
```shell
ssh pi@<ip-addr-of-rpi>
```
Turning on SSH by default we get the default Raspberry Pi ssh credentials of `pi` and `raspberry` respectively. 
Prior to anything else, let's delete this user and add one of our own with slightly better security.


```shell
sudo adduser <mynewuser>
```

Then we can set the password and confirm the changes:
```shell
Adding user `<mynewuser>' ...
Adding new group `<mynewuser>' (1001) ...
Adding new user `<mynewuser>' (1001) with group `<mynewuser>' ...
Creating home directory `/home/<mynewuser>' ...
Copying files from `/etc/skel' ...
New password:
```

Next, since this user will need `sudo` let's grant that:
```shell
usermod -aG sudo <mynewuser>
```

Finally, let's delete the default user:
```shell
userdel -r pi
```



### Static IP

IP Binding in router

Starting in headlessmode
Add SSH file to boot image
Set IP on each device


### Finishing Day 1

Do this `n` more times for the `n` more Pis.

## 

## Day 2

## Day 3

To start, we'll need a container runtime. I use Docker at work so let's use that here:

Docker
```shell
TODO install Docker
```

Kubernetes
```shell
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
echo "$(<kubectl.sha256) kubectl" | sha256sum --check
```
Expecting `kubec: ok`

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


