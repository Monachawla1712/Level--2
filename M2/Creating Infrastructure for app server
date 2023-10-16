# To create a multi-instance infrastructure for Wordpress application for High availability.

## First Install apache and php.

#### Start by updating the package manager cache. Open a terminal and run this command:
      # sudo apt-get update
      
### Install Apache
Run this command to install the apache package on ubuntu:

      # sudo apt-get install apache2

### Start your Apache webserver

      # systemctl start apache2

### Verify Apache Installation 
   - open a web browser and type in the address bar http://server_ip_address
   - check the  status of your apache webserver

### Installing PHP
    # sudo apt install php libapache2-mod-php php-mysql

### Check the version of php
    # php -v

### Installing additional PHP extensions.
    ## WordPress and many of its plugins, however, leverage additional PHP extensions.
    #sudo apt install php-curl php-gd php-mbstring php-xml php-xmlrpc php-soap php-intl php-zip

### Restart apache2.
    # sudo systemctl restart apache2

### Adjusting Apache’s Configuration to Allow for .htaccess Overrides and Rewrites

## Enabling .htaccess Overrides

    # sudo vim /etc/apache2/sites-available/wordpress.conf
    <VirtualHost *:80>
. . .
    <Directory /var/www/wordpress/>
        AllowOverride All
    </Directory>
. . .
</VirtualHost>

## Enabling the Rewrite Module
    # sudo a2enmod rewrite

## Enabling the changes
    # sudo apache2ctl configtest

You may receive output like the following:

Output
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
Syntax OK

## Restart the apache :

    # sudo systemctl restart apache2

## Download the wordpress on ubuntu : 
 # cd /tmp

## Then download the compressed release with the following curl command:
    # curl -O https://wordpress.org/latest.tar.gz

## Extract the compressed file to create the WordPress directory structure:
    # tar xzvf latest.tar.gz

## Configuring the wordpress directory:

  ## Now set appropriate permissions , It should be owned by the Apache2 user and group called www-data.
    # sudo chown -R www-data:www-data /var/www/wordpress
    # sudo chmod -R 775 /var/www/wordpress

## Setting Up the WordPress Configuration File:
    # curl -s https://api.wordpress.org/secret-key/1.1/salt/

You will receive unique values that resemble output similar to the following

Output
define('AUTH_KEY',         '1jl/vqfs<XhdXoAPz9 DO NOT COPY THESE VALUES c_j{iwqD^<+c9.k<J@4H');
define('SECURE_AUTH_KEY',  'E2N-h2]Dcvp+aS/p7X DO NOT COPY THESE VALUES {Ka(f;rv?Pxf})CgLi-3');
define('LOGGED_IN_KEY',    'W(50,{W^,OPB%PB<JF DO NOT COPY THESE VALUES 2;y&,2m%3]R6DUth[;88');
define('NONCE_KEY',        'll,4UC)7ua+8<!4VM+ DO NOT COPY THESE VALUES #`DXF+[$atzM7 o^-C7g');
define('AUTH_SALT',        'koMrurzOA+|L_lG}kf DO NOT COPY THESE VALUES  07VC*Lj*lD&?3w!BT#-');
define('SECURE_AUTH_SALT', 'p32*p,]z%LZ+pAu:VY DO NOT COPY THESE VALUES C-?y+K0DK_+F|0h{!_xY');
define('LOGGED_IN_SALT',   'i^/G2W7!-1H2OQ+t$3 DO NOT COPY THESE VALUES t6**bRVFSD[Hi])-qS`|');
define('NONCE_SALT',       'Q6]U:K?j4L%Z]}h^q7 DO NOT COPY THESE VALUES 1% ^qUswWgn+6&xqHN&%');

## Next, open the WordPress configuration file:
    # sudo vim /var/www/wordpress/wp-config.php

Go to this file and paste the unique values whose output got in previous command.
. . .

define('AUTH_KEY',         'put your unique phrase here');
define('SECURE_AUTH_KEY',  'put your unique phrase here');
define('LOGGED_IN_KEY',    'put your unique phrase here');
define('NONCE_KEY',        'put your unique phrase here');
define('AUTH_SALT',        'put your unique phrase here');
define('SECURE_AUTH_SALT', 'put your unique phrase here');
define('LOGGED_IN_SALT',   'put your unique phrase here');
define('NONCE_SALT',       'put your unique phrase here');


In the same file of wp-config.php , change the database settings. DB_NAME, DB_USER and DB_PASSWORD , DB_HOST
. . .

// ** MySQL settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define( 'DB_NAME', 'wordpress' );

/** MySQL database username */
define( 'DB_USER', 'wordpressuser' );

/** MySQL database password */
define( 'DB_PASSWORD', 'password' );

/** MySQL hostname */
define( 'DB_HOST', 'localhost' );

/** Database Charset to use in creating database tables. */
define( 'DB_CHARSET', 'utf8' );

/** The Database Collate type. Don't change this if in doubt. */
define( 'DB_COLLATE', '' );
...

Save the file. 

Wordpress Installation is done.....


