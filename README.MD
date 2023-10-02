## Hyperledger Fabric - GCP - Kubernetes

### I am using GCP for setting up the project 

**1. Create a VM Instance **

**2. Use SSH to connect to your VM instance.**

Open Google Cloud Shell 

List your VM instances
`gcloud compute instances list`

Identify the VM you want to connect to:

SSH into the VM:
`gcloud compute ssh [INSTANCE_NAME] --zone [ZONE]`

#### Update the System:
`sudo apt update`
`sudo apt upgrade -y`

Install NFS Server Package:
`sudo apt install nfs-kernel-server`

Create nfs_share folder
`sudo mkdir -p /mnt/nfs_share`

give permistions
`sudo chown -R nobody:nogroup /mnt/nfs_share/`
`sudo chmod 777 /mnt/nfs_share/`

check permistion if you want by using these cmd
`ls -lt /mnt/nfs_share`

see config using this cmd
`car /etc/exports`

add some code to the exports folder
`echo /mnt/nfs_share *(rw,sync,no_subtree_check,insecure) | sudo tee -a /etc/exports`

you can check exports file for the updated content 
`car /etc/exports`

if you want change permistion use this cmd
`chmod +w /path/to/readonly_file`

------------


## Now setting up NFS Client Server

#### Update the System:
`sudo apt update`
`sudo apt upgrade -y`

install nfs common package
`sudo apt install nfs-common`

Create folder for nfs_clientshare inside mnt folder
`sudo mkdir -p /mnt/nfs_clientshare`

Mount the NFS Share
`sudo mount -t nfs <IP>:/mnt/nfs_share /mnt/nfs_clientshare`

Check the mounting usign this cmd
`df -h`


------------










