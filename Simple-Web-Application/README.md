Creating a Simple Web Application using Docker :

1. Download the Simple-Web-Application files and save them in the same directory
2. Open CMD and traverse to the Simple-Web-Application
3. Run command -->  docker build .  ( Dont forget the "." )
4. Next you have to run this command --> docker build -t dockerid/directoryname .
5. Docker id is the id you have to create from the hub.docker.com
6. Directory name is the name of the directory in which you have stored the files
7. Now you have to execute this command in CMD --> docker run -t dockerid/directoryname
8. Next execute this command -->  docker run -p 8080:8080 dockerid/directoryname
9. Now open your browser and type --> localhost:8080
10. You will be successfully running the web application on your browser and get the message of " HI THERE "

