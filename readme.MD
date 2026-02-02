### Jenkins Setup

partition disk
..
growpart /dev/nvme0n1 4

lvextend -L +10G /dev/mapper/RootVG-varVol
lvextend -L +10G /dev/mapper/RootVG-rootVol
lvextend -l +100%Free /dev/mapper/RootVG-homeVol

xfs_growfs /
xfs_geowfs /var
xfs_growfs /home

Installation steps for jenkins setup
...
sudo curl -fsSL https://pkg.jenkins.io/redhat-stable/jenkins.repo -o /etc/yum.repos.d/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key

sudo yum install fontconfig java-21-openjdk -y
sudo yum install jenkins -y
sudo systemctl daemon-reload

#### Plugins
* Stage View

#### Master Agent Architecture
* create credentials to connect agent
* Install Java in agent
* Select non verification strategy