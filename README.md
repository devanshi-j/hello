# hello
HOW TO INSTALL OPENSTACK ON UBUNTU WITH DEVSTACK..

What is OpenStack?
OpenStack is a free, open standard cloud computing platform. It is mostly deployed as infrastructure-as-a-service in public and private clouds where virtual servers and other resources are available to users.

Whats is DevStack?
Devstack is a series of scripts used to quickly bring up a complete OpenStack environment. We can download the latest version of OpenStack from the git master branch. It used to set up a faster and quicker way to set up the development environment and as the basis for most of the OpenStack project functional testing.

Minimum Requirements
Before we begin, ensure you have the following minimum prerequisites

1. A fresh Ubuntu 22.04 installation
2. User with sudo privileges
3. 4 GB RAM
4. 2 vCPUs
5. Hard disk capacity of 10 GB
6. Internet connection

Step 1: Update and Upgrade the System
 apt update -y && apt upgrade -y

 Step 2: Create Stack user and assign sudo priviledge
sudo adduser -s /bin/bash -d /opt/stack -m stack
sudo chmod +x /opt/stack


Next, run the command below to assign sudo privileges to the user

echo "stack ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/stack

Step 3: Install git and download DevStack
Once you have successfully created the user ‘stack’ and assigned sudo privileges, switch to the user using the command.
su - stack


In most Ubuntu 22.04 systems, git comes already installed. If by any chance git is missing, install it by running the following command.
sudo apt install git -y


Using git, clone devstack’s git repository as shown.
git clone https://git.openstack.org/openstack-dev/devstack

Step 4: Create devstack configuration file
In this step, navigate to the devstack directory.
cd devstack


Then create a local.conf configuration file.
vim local.conf
Paste the following content

[[local|localrc]]
# Password for KeyStone, Database, RabbitMQ and Service
ADMIN_PASSWORD=StrongAdminSecret (SET UP YOUR OWN PASSWORD)
DATABASE_PASSWORD=$ADMIN_PASSWORD
RABBIT_PASSWORD=$ADMIN_PASSWORD
SERVICE_PASSWORD=$ADMIN_PASSWORD
# Host IP - get your Server/VM IP address from ip addr command
HOST_IP=10.208.0.10  (REPLACE THIS WITH YOUR OWN PRIVATE IP)


Step 5: Install OpenStack with Devstack
To commence the installation of OpenStack on Ubuntu 22.04, run the script below contained in devstack directory.
./stack.sh


The following features will be installed:

1.Horizon — OpenStack Dashboard
2.Nova — Compute Service
3.Glance — Image Service
4.Neutron — Network Service
5.Keystone — Identity Service
6.Cinder — Block Storage Service
7.Placement — Placement API


Step 6: Accessing OpenStack on a web browser
JUST PASTE THE PUBLIC IP OF YOUR INSTANCE IN YOUR BROWSER.

