# Ubuntu SSH Enable Docker Container

# USE

- Run the container:

docker run -it -d yasint/ubuntu-ssh-enabled

Identify the Internal IP

docker inspect <container-id-name>

SSH

ssh <container-ip> 172.17.0.2

Username: root

Password: 1234