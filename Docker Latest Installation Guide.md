### Docker installation-

1. Run the following command to remove any old and unwanted docker files form our machine as we will need latest version so as not to face any compatibility issue.
Your Linux distribution may provide unofficial Docker packages, which may conflict with the official packages provided by Docker.
If u have and specific version already installed that u need which is very old you might face some issues.


```
sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-compose-v2 docker-doc podman-docker containerd runc | cut -f1)
```

Also, to remove any previous config files run following command.

```
sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-compose-v2 docker-doc podman-docker containerd runc | cut -f1)

```

2. Install using the `apt` repository.
Before you install Docker Engine for the first time on a new host machine, you need to set up the Docker `apt` repository. Afterwards, you can install and update Docker from the repository.

```
# Add Docker's official GPG key:
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update
```

3. To install the latest version, run-

```
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

Some systems may have this behaviour disabled and will require a manual start-

```
sudo systemctl start docker
```

Note-
Your don't need a specific version of docker for our case, but if you do, you can check our the official page of docker below just for that.

[Docker Official Website](https://docs.docker.com/engine/install/ubuntu/)

4. To check whether docker is running or not we will write a simple Hello world program.
```
sudo docker run hello-world
```

This will download and run a container, check thing and them display "Hello world" as output.
It you don't get a input you will need to re-install docker once again.

5. Adding docker to sudo group.

```
sudo groupadd docker
sudo usermod -a -G docker $USER
```
This will allow your current user to run docker commands without having to enter sudo every time.