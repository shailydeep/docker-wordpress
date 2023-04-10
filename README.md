# docker-wordpress
What/Why is Docker Compose
Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application’s services. Then, with a single command, you create and start all the services from your configuration.

Let’s understand with a simple example, When you are working in the real-time industry there may be a requirement where you need to design an application that has web-tier and data-base tier and if you want to design such application using docker, you need to create two or more container as per the requirement.



So, let’s dockerize a sample word press application which has a web tier and database tier. In word press application we define instructions inside a YAML file and those steps in the YAML file give information to the web tier about the database.

Steps to dockerize word press application:

First, we need to make the database container UP and the command to make the data-base container up is:
$ docker container run --name some-mysql -e MYSQL_ROOT_PASSWORD=mypassword -d mysql:5.7
Get the IP address of data-base container using command below command from field “IP Address”
$ docker container inspect <first 4-digit container id>
Now, we need to run a web-tier container using the below command, suppose 172.17.0.2 is the database container's IP address
$ docker container run --name wordpress -e WORDPRESS_DB_HOST=172.17.0.2:3306 -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=mypassword -d wordpressget the IP of the web-tier container as explained in Step 2.
After getting the web-tier IP address, you can access the WordPress application by giving the IP address in the URL.
