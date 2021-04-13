osticket - Installation
========================================================

# Introduction

Docker image for OSTicket ---> (http://osticket.com/).

OSTicket is being served by nginx (http://wiki.nginx.org/Main) using PHP-FPM (http://php-fpm.org/) with PHP 7.2.
PHP7's mail (http://php.net/manual/en/function.mail.php) function is configured to use msmtp (http://msmtp.sourceforge.net/) to send out-going messages.


# How to run :

Ensure you have a MySQL 5+ container running that OSTicket can use to store its data.

If not, get it by typing the following command :

docker pull mysql

This will pull the mysql image. Later, just run it from the docker dashboard before running the following.

Now run this command :

docker run --name osticket_mysql -d -e MYSQL_ROOT_PASSWORD=secret -e MYSQL_USER=osticket -e MYSQL_PASSWORD=secret -e MYSQL_DATABASE=osticket mysql:5


Now run this image and link the MySQL container.


docker run --name osticket -d --link osticket_mysql:mysql -p 8080:80 campbellsoftwaresolutions/osticket


Wait for the installation to complete then browse to your OSTicket staff control panel at `http://localhost:8080/scp/`. Login with default admin user & password:

* username: **ostadmin**
* password: **Admin1**

Now configure as required. If you are intending on using this image in production, please make sure you change the
passwords.

And if you want to change the environmental database variables on the OSTicket image to run, you can do it as follow :

docker run --name osticket -d -e MYSQL_ROOT_PASSWORD=new_root_password -e MYSQL_USER=new_root_user -e MYSQL_PASSWORD=new_secret -e MYSQL_DATABASE=osticket --link osticket_mysql:mysql -p 8080:80 campbellsoftwaresolutions/osticket




