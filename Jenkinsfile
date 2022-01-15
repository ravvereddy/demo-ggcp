#!/bin/bash
wget https://s3.amazonaws.com/aaronsilber/public/authbind-2.1.1-0.1.x86_64.rpm
sudo rpm -Uvh https://s3.amazonaws.com/aaronsilber/public/authbind-2.1.1-0.1.x86_64.rpm
sudo touch /etc/authbind/byport/80
sudo chmod 500 /etc/authbind/byport/80
sudo chown ec2-user /etc/authbind/byport/80
pip3 install virtualenv
cd /home/ec2-user/app
virtualenv environment
source environment/bin/activate
pip3 install -r requirements.txt
