# s3-docker-k8s-explorations
Docker and Kubernetes explorations

This project is built to practice using a multi-container docker deployment pipeline. On its surface, it is just a fibonacci calculator. In order to determine and communicate the fibonacci number for a given index, it uses the following services.

Node API server
Node worker service
Redis
Postgres
Nginx
React UI
It will be deployed to AWS Elastic Beanstalk using Travis CI and Dockerhub.

For development, I wrote a .travis.yml file that builds the docker images, runs tests, and pushes the images up to docker hub.

I used AWS Elastic Beanstalk multi-container deployment and wrote a Dockerrun.aws.json file that maps the containers in the docker-compose.yml to the AWS environment. The Dockerrun file pulls the images from Docker Hub so that I don't have to build them in the production enviroment.

I set up a Postgres service with AWS RDS.


Steps to run :

cd fibonacci-series

cd client

docker build -f Dockerfile.dev .

cd ..

cd server 

docker build -f Dockerfile.dev .

cd ..

cd worker 

docker build -f Dockerfile.dev .

cd ..

fibonacci-series> docker-compose up --build

It will start accepting connections.

Finally,

Go to your browser and type :

localhost:3050 

and it will display the fibonacci application.

