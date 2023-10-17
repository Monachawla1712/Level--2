# To mount the EFS with the App server ( Wordpress)

## Create File system.
1. give a name and attach VPC.
2. Click on customize.
3. In storage class section, choose standard and then click on next in the last.
4. In the network access section, choose vpc.
5. In mount targets, give the availability zone, subnet ID and attach security group that is created for EFS( enabled port for efs in security group)
6. click on next, next and create.
7. Then go to attach by clicking the file system that is created.

## Go to wordpress instance.
## To build and install amazon-efs-utils as a Debian package for Ubuntu and Debian.

 1. (Optional) Apply updates before installing the package with the following command:

           sudo apt-get update
           Install updates as needed.

  2. Install git and binutils, using the following command. binutils is required for building DEB packages,

          sudo apt-get -y install git binutils
        
  3. Clone amazon-efs-utils from GitHub using the following command.

          git clone https://github.com/aws/efs-utils

  4. To build and install the amazon-efs-utils DEB package

## Navigate to the directory that contains the amazon-efs-utils package.

         cd /var/www/wordpress/wp-content/efs-utils/
  
  5. Build amazon-efs-utils using the following command:

            ./build-deb.sh
 
   6. Install the package with the following command.
      
            sudo apt-get -y install ./build/amazon-efs-utils*deb

### Mount manually :
      sudo mount -t efs file_system_id folder/
      
      df -h

### For unmount:
     sudo unmount file_system_id folder/
     
     df -h

### For Permanent mounting:
     Go to vim /etc/fstab type this line and save it.

     file_system_id.efs.aws-region.amazonaws.com:/ mount_point nfs4 nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport,_netdev 0 0

     mount -a
     
     df -h

same set up done in both wordpress..........

 


