Install Docker and check the version :

docker --version

Create a new directory on your Desktop and clone the repo into it :

cd ~/Desktop
git clone https://github.com/S3Infosoft/s3-docker-k8s-explorations.git
cd Python-Django-Project-in-Docker


Install the software packages specified by Pipenv and start a new shell :

pipenv install
pipenv shell
(Python-Django-Project-in-Docker) $

Migrate our database after these changes :

(Python-Django-Project-in-Docker) $ python manage.py migrate

Now use the python manage.py runserver command and go to browser and check :

http://localhost:8000

Start the Docker container using the up command:

docker-compose up -d --build

Docker is all set . 

Visit the Message Board homepage at http://127.0.0.1:8000/

Now we need to update our Python app to use PostgreSQL instead of SQLite :

1. pipenv install psycopg2-binary
2. docker-compose exec web python manage.py migrate
3. docker-compose exec web python manage.py createsuperuser

Now go to http://127.0.0.1:8000/admin and login.

We can add new posts via the admin and then seem them on the homepage.




