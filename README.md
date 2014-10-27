docker-sabnzbd-i386
===================

Docker image for SABnzbd on Ubuntu i386/32-bit, so suitable for 32-bit Docker hosts (yes, those do exist!).

Based on:
- SABnzbd docker image for x86_64 by Tim Haak (https://github.com/timhaak/docker-sabnzbd)
- 32-bit docker Ubuntu image by shawn (docker hub: shawn/ubuntu-precise-i386)

How to use this:

First: make sure port 8080 is not in use (for example by another SABnzbd instance on the host or in a docker container)

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

Then click on "Save Changes". This step is important, because only that way the downloaded stuff is saved to the real filesystem (= filesystem of the host), instead of staying inside the docker container (and thus getting lost after stopping the container).

Now do a real download. You should then inspect the results this way:
```
sudo ls -al /root/sabnzbd-config
sudo ls -al /root/sabnzbd-data/complete
```

Happy downloading.




