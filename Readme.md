# Ansible repo for Homelab

I have some services running in my homelab and I use this repo to manage all of them. These services either run as a systemd service or containers. Currently these services exist.  

Containers run in a custom docker bridge network and are therefore resolvable using container names. For example, for prometheus to gather cAdvisor metrics, it can use cadvisor:8080/metrics endpoint. This approach removes the need for port mapping and allows using names instead of IPs, which is memorable. This also avoids the use of __uncessary NAT__.  

Containers use docker volumes for application managed data, and bind mounts for the data that needs backup or to be changed manually. Volumes and database are backed up using systemd services/timers.

Packet flow: __Client__ &rarr; __Pi-hole__ &rarr; __Nginx__ &rarr; __application__

Systemd role: used to create new services or manage existing ones. Deploy docker: used to manage containers