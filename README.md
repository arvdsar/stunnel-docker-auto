# stunnel-docker-auto

I use this Stunnel container to run Stunnel on Docker on my Synology NAS.
Using Stunnel I can provide SSL frontend for i.e. Domoticz and NodeRed.

I've created this Dockerfile to generate an Ubuntu based container with Stunnel to run on my Synology NAS. It should work on other devices too.

You can build an image yourself using this Dockerfile running:
docker build -t yourname/stunnel .

You can also download my image from within the Synology Docker manager. Search for 
mrmadalex:stunnel

Mount a local path to /etc/stunnel and store the stunnel.conf and certificates in that local folder.
i.e.: I have shared folder on my synology named: 'Docker', so I mount /etc/stunnel to docker/stunnel on my NAS.

When running from commandline it would be something like:

docker run mrmadalex/stunnel -v /etc/stunnel:yourpath/stunnelfiles -p 443:443 

On the Synology you have to create a new bridged network so all the containers within that new network can find each other on host/container name.

Use the stunnel.conf as an example and expose the proper network ports you need for INCOMMING requests.

