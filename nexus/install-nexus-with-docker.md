# Installation with docker image:

https://hub.docker.com/r/sonatype/nexus3/

- Do not forget mounting volume before run!

$ docker pull sonatype/nexus3

$ docker volume create --name nexus-data

$ docker run -d -p 8081:8081 --name nexus -v nexus-data:/nexus-data sonatype/nexus3
