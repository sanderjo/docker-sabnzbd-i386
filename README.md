docker-sabnzbd-i386
===================

Docker image for SABnzbd on Ubuntu i386/32-bit, so suitable for 32-bit hosts

Based on:
- SABnzbd docker image for x86_64 https://github.com/timhaak/docker-sabnzbd
- 32-bit docker Ubuntu image by shawn, known as shawn/ubuntu-precise-i386

How to use this:

First: make sure port 8080 is not in use (for example by another SABnzbd instance)

Then:
```
git clone https://github.com/sanderjo/docker-sabnzbd-i386.git
cd docker-sabnzbd/

sudo mkdir /root/sabnzbd-config
sudo mkdir /root/sabnzbd-data

sudo docker build -t sabnzbd-i386 .

sudo docker run -d -h sabnzbd-superbox  -v /root/sabnzbd-config:/config -v /root/sabnzbd-data:/data -p 8080:8080 -p 9090:9090 sabnzbd-i386

sudo docker ps

```
Then point your webbrowser to http://localhost:8080/ and fill out the wizard.

After filling out the wizard, do a test download. If that works, do an important thing: Go to http://localhost:8080/config/folders/ and fill out:
- Temporary Download Folder: /data/incomplete
- Completed Download Folder: /data/complete
Save this info. This step is important, because only that way the downloaded stuff is saved to the real filesystem (= filesystem of the host), instead of staying inside the docker container (and thus getting lost after exiting the container).


