# jira + confluence via docker-compose

Plan of steps:
1. You must install Docker + Docker-compose
2. You need to configure service jira, confluence in docker-compose.yml, so that you can connect to both services via dns. Set up sync between jira, confluence

Cope with the first task was not with great difficulty. To install Docker, I chose Cent OS, considering that it is for Red Hat derivatives that its support is the best.
How I did it you can read [here] (https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-centos-7)

The second task can be divided into several subtasks:
1. Run proxy
In production environments, it is common practice to launch a container on port 80 and use the assigned DNS name.
You can run Jira behind a proxy server, and you can run other applications on the same Docker host, for example, Confluence.
<p align = "center">
  <img src = "https://github.com/eleutherius/docker-test/raw/master/docker-proxy.png" width = "666" />
</ p>

To make it easier, you can run this container with the VIRTUAL_HOST environment variable. This variable will change the Tomcat server configuration for the proxy request.

## How to start ? 

```
docker-compose up -d --f
```
