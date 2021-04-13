## OpenKM Installation

This is an unofficial container that provides the OpenKM application with persistent data.

To quickly pull and run the application, exectute the following:

`docker run -p 8080:8080 mbagnall/openkm`

To add document and account persistency, use the following. Note that you will need to use this command in order for the installation not to re-initializa on every container rebuild or update.

`docker run -p 8080:8080 -v./openkm-data:/opt/tomcat-8.5.34/repository mbagnall/openkm`


Once you have started the containers, you must alter the grants on the mysql server manually. This must be done BEFORE going to OpenKM for the first time or your install will be broken. To alter the grants, log into your mysql contaner as root:

`docker exec -ti openkm-datastore bash`

Then login to your MySQL server as root:

`mysql -uroot -pOpenKM77`

Finally, change the grants:

`GRANT ALL ON okmdb.* TO 'openkm'@'%' WITH GRANT OPTION;`

After these steps are completed, go to the URL of your OpenKM server and everything should work. The default administrative user and password is as follows:

**Username:** okmAdmin  
**Password:** admin

