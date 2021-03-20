Install Sentrifugo HRM on Ubuntu Server :

1. Install Necessary Dependencies :
  
  Log in to your Ubuntu Server and first install the MariaDB database with the command:
    
      sudo apt-get install mariadb-server -y
  
  Create a password for the admin user and answer the questions to complete the process.
  
  Install the remaining dependencies. Do this with the command:
  
      sudo apt-get install apache2 php7.2 libapache2-mod-php7.2 php7.2-common php7.2-mbstring php7.2-xmlrpc php7.2-soap php7.2-gd php7.2-xml php7.2-intl php7.2-mysql php7.2-cli php7.2 php7.2-ldap php7.2-zip php7.2-curl unzip wget -y
      
  Start and enable both the database and web servers with the command:
  
       sudo systemctl start mariadb
       sudo systemctl enable mariadb
       sudo systemctl start apache2
       sudo systemctl enable apache2
       
2. Configure the database :

    Log in to the database server with the command:
    
       sudo mysql -u root -p
       
    Create the database with the command:
    
       CREATE DATABASE sentrifugodb;
       
    Create a new user and give it full permissions to the new database with the commands:
    
        CREATE USER 'sentrifugo'@'localhost' IDENTIFIED BY 'PASSWORD';
        GRANT ALL ON sentrifugodb.* TO 'sentrifugo'@'localhost' IDENTIFIED BY 'PASSWORD' WITH GRANT OPTION;
        
    Finalize the database with the commands:
    
        FLUSH PRIVILEGES;
        exit
        

3. Download and install Sentrifugo :

    Download and install Sentrifugo. Download the necessary file with the command:
    
        wget http://www.sentrifugo.com/home/downloadfile?file_name=Sentrifugo.zip -O Sentrifugo.zip
        
    Unzip it with the command:
    
        unzip Sentrifugo.zip
        
    Move the file and give it the necessary permissions with the commands:
    
        sudo cp -r Sentrifugo_X /var/www/html/sentrifugo
        sudo chown -R www-data:www-data /var/www/html/sentrifugo/
        sudo chmod -R 755 /var/www/html/sentrifugo/
        
    Open the Sentrifugo configuration file for editing with the command:
      
        sudo nano /var/www/html/sentrifugo/application/configs/application.ini
        
    Locate the line:
    
        phpSettings.error_reporting = E_All
        
    Change that line to:
    
        phpSettings.error_reporting = E_ALL & ~E_DEPRECATED & ~E_STRICT
        
    Create the Apache virtual host file with the command:

        sudo nano /etc/apache2/sites-available/sentrifugo.conf
        
        
    In that file, paste the following:

        <VirtualHost *:80>
        ServerAdmin admin@example.com
        DocumentRoot /var/www/html/sentrifugo
        ServerName example.com
        ServerAlias www.example.com

        <Directory /var/www/html/sentrifugo/>
         Options +FollowSymlinks
        AllowOverride All
        Require all granted
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        </VirtualHost>
        
    Edit the config file as needed, and then save/close the file.

    Enable the newly created site and the rewrite module with the commands:

        sudo a2ensite sentrifugo
        sudo a2enmod rewrite

   Reload Apache with the command:

        sudo systemctl reload apache2

   Before we launch the web-based installer, there's a PHP function that has been deprecated. To fix this, open the config file with the command:

        sudo nano /var/www/html/sentrifugo/install/PHPMailer/PHPMailerAutoload.php
        
        
   In that file, replace the line:

        function __autoload($classname)
     
   With:

        function spl_autoload_register()
        
   Save and close the file.

   Finally, point a web browser to http://SERVER_IP/sentrifugo (where SERVER_IP is the IP address of the hosting server).
   We will be greeted by the web-based installer, where we can easily complete the installation.
   
   Click link to open the Sentrifugo login, and use the credentials displayed on the success page.
   
   Now we are ready to start using your new Sentrifugo HRM solution.
   
   
   
   
