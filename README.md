docker-sabnzbd-i386
===================

Docker image for SABnzbd on Ubuntu i386/32-bit, so suitable for 32-bit hosts

Based on:
SABnzbd image for x86_64 https://github.com/timhaak/docker-sabnzbd
Ubuntu 32-bit image by shawn, known as shawn/ubuntu-precise-i386

How to use this:
```
git clone https://github.com/timhaak/docker-sabnzbd.git
cd docker-sabnzbd/

sudo mkdir /root/sabnzbd-config
sudo mkdir /root/sabnzbd-data

sudo docker build -t sab-testing .

sudo docker run -d -h sabnzbd-superbox  -v /root/sabnzbd-config:/config -v /root/sabnzbd-data:/data -p 8080:8080 -p 9090:9090 sab-testing

sudo docker ps

```
Then your webbrowser to http://localhost:8080/ and fill out the wizard
