# C9-Docker-Compose
Deploy C9-IDE Inside Docker Container

## Provisioning Your Linux VM

Install docker.io
```
$ sudo apt update && sudo apt upgrade
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$ sudo apt-key fingerprint 0EBFCD88
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```
Install Docker-Compose
```
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.26.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
```
```
Clone Repository Ini ke dalam folder home /c9users/
$ sudo adduser c9users
$ git clone https://github.com/nicolasjulian/C9-Docker-Compose.git /home/c9users/
```
How to use ? :

```
$ sudo su #Login as root or priviledge user
$ cd /home/c9users/
$ vi .env #Edit Port, Nama pelanggan setiapkali membuat ingin user baru
$ sudo docker-compose -p kamarudin up -d
```
### Explaination

> File .env
>
> There is 3 variables inside file .env :
> - PORT=
> - PASSWORD_PELANGGAN=
> - NAMA_PELANGGAN=
>
> **PORT=** is used to specify the port where the container will be exposed, so make sure change this variable everytime you crate new c9IDE
>
> **NAMA_PELANGGAN=** is used to set username login, and directory name which will to mount to docker container
>
> **PASSWORD_PELANGGAN=** is used to set password for authenticate to c9Core

> How to use ?
>
> *sudo docker-compose -p kamarudin up -d*
>> **sudo** use to call the priviledge user in this case is root user
>>
>> **docker-compose** to execute the docker-compose binary file
>>
>> **-p xxxx** use to specify the project name, this parameter will separated your client container to other project. So make sure you change this parameter to each your container IDE
>>
>> **up** to Create and start containers
>>
>> **-d** to Detached mode: Run containers in the background, print new container names

> Optinal variables
>
> There is 2 variables inside file .env :
> - **CPUS=**
> - **MEMORY=**
>
> **CPUS=** is used to specify how much limit CPU core will be used. If limit reached, container will be restart, and terminate all session. i.e. 0.5 is euqals to 1/2 of 1 core cpu and 2 is equals of 2 core full of cpus
>
> **MEMORY=** is used to specify how much limit ram will be used, limit ram is maximum load. If limit reached, container will be restart, and terminate all session.
