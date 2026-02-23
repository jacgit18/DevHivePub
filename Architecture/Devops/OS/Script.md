---
tags:
  - linux
author:
  - jacgit18
  - chatgpt
Comments: 
Purpose: 
Status: Draft
Started: 
EditDate: 2024-03-11
Relates: 
dg-publish:
---
Certainly! Here's an example of a Bash install script that installs essential software and tools for software engineers:

```bash
#!/bin/bash

# Update package lists
sudo apt update

# Install Git
sudo apt install git -y

# Install Node.js and npm
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
sudo apt install -y nodejs

# Install Python 3 and pip
sudo apt install python3 python3-pip -y

# Install Visual Studio Code
curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -o root -g root -m 644 packages.microsoft.gpg /etc/apt/trusted.gpg.d/
sudo sh -c 'echo "deb [arch=amd64 signed-by=/etc/apt/trusted.gpg.d/packages.microsoft.gpg] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
sudo apt update
sudo apt install code -y

# Install Docker
sudo apt install docker.io -y
sudo usermod -aG docker $USER

# Install Postman
sudo snap install postman

# Install Heroku CLI
curl https://cli-assets.heroku.com/install-ubuntu.sh | sudo sh

# Install AWS CLI
sudo apt install awscli -y

# Install curl and wget
sudo apt install curl wget -y

# Install jq
sudo apt install jq -y

# Install PostgreSQL
sudo apt install postgresql postgresql-contrib -y

# Install MongoDB
sudo apt install mongodb -y

# Install Redis
sudo apt install redis-server -y

# Install Apache Kafka
sudo apt install default-jre -y
wget https://downloads.apache.org/kafka/2.8.0/kafka_2.13-2.8.0.tgz
tar -xzf kafka_2.13-2.8.0.tgz
rm kafka_2.13-2.8.0.tgz

# Install MySQL
sudo apt install mysql-server -y

# Install Vim
sudo apt install vim -y

# Install Zsh and Oh My Zsh
sudo apt install zsh -y
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Install Powerline fonts
sudo apt install fonts-powerline -y

# Clean up
sudo apt autoremove -y
sudo apt clean

echo "Software installation completed!"
```

Save the script into a file, for example, `install.sh`. Make the file executable with the following command:

```bash
chmod +x install.sh
```

Then, you can run the script by executing:

```bash
./install.sh
```

