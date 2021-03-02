# HOMELAB: THE JOURNAL

![yup](1point21.png)

## Day 0: Shopping list

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

## Day 1: Connecting the bits and bops

### Headless Pi:

Lazy programmers are good programmers. Since we're good programmers let's by lazy and not bother with plugin in a monitor, mouse and keyboard into our Pi and stay comfortable in the our chairs.

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


### Docker, K8s and Helm

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

### Finishing Day 1

Do this `n` more times for the `n` more Pis.

## Day 2: Setting Up the Cluster

## Day 3: A little cleanup with PoE

Power over Ethernet (PoE), in short, is a technology that enables network cables to carry electrical power. If you want to learn more about it see [here](https://en.wikipedia.org/wiki/Power_over_Ethernet).  In order to provide PoE to the Pis in the cluster we will need some aditional hardware.
[PoE Hats] (https://www.pishop.us/product/raspberry-pi-poe-hat/) provide exactly this mechanism; I'll take four, please. 

(pics)

Ok, this is all about cleeaner now that we have four cables out of the way. Well, it's been a long work day so that concludes <strong>Day 3</strong>.
