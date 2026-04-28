To get started, you will need following things-
1. Docker installed and working.
2. sudo access on the machine that will host your Portainer Server instance.
3. By default, Portainer Server will expose the UI over port `9443` and expose a TCP tunnel server over port `8000`. The latter is optional and is only required if you plan to use the Edge compute features with Edge agents.

### Step 1-
To install using `docker run`, first create the volume that Portainer Server will use to store its database-
```
docker volume create portainer_data
```
By default, Portainer generates and uses a self-signed SSL certificate to secure port `9443`.  you can provide your own SSL certificate after installation is complete.

### Step 2-
Download and install docker-
```
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:sts
```

### Step 3-
```
docker ps
```
To check Portainer Server container has been created started running.

### Step 4-
Go to your browser and type-
```
https://localhost:9443
```
After that create login credentials and you are done.