# Installation

# t2.medium instance
# security_group 22--8081

sudo yum update -y

# java

sudo yum install java-1.8.0-openjdk -y
java -version

# maven

sudo wget https://repos.fedorapeople.org/repos/dchen/apache-maven/epel-apache-maven.repo -O /etc/yum.repos.d/epel-apache-maven.repo

ls /etc/yum.repos.d/

sudo sed -i s/\$releasever/6/g /etc/yum.repos.d/epel-apache-maven.repo

cd /opt

sudo yum install apache-maven -y

mvn -version

whereis mvn

# nexus

sudo wget -O nexus.tar.gz https://download.sonatype.com/nexus/3/latest-unix.tar.gz

sudo tar xvzf nexus.tar.gz

sudo rm nexus.tar.gz

sudo mv nexus-3* nexus

sudo chown -R ec2-user:ec2-user /opt/nexus

sudo chown -R ec2-user:ec2-user /opt/sonatype-work


sudo nano /opt/nexus/bin/nexus.rc

\\\\\\\\\\\

run_as_user="ec2-user"

\\\\\\\\\\\

export PATH=$PATH:/opt/nexus/bin

echo $PATH

cd /opt

nexus start

nexus stop

cd nexus/bin

sudo nano /etc/systemd/system/nexus.service


\\\\\\\\\\\\\

[Unit]

Description=nexus service

After=network.target

[Service]

Type=forking

LimitNOFILE=65536

User=ec2-user

Group=ec2-user

ExecStart=/opt/nexus/bin/nexus start

ExecStop=/opt/nexus/bin/nexus stop

User=ec2-user

Restart=on-abort

[Install]

WantedBy=multi-user.target

\\\\\\\\\\\


sudo systemctl daemon-reload

sudo systemctl start nexus.service

sudo systemctl enable nexus.service

sudo systemctl status nexus.service

