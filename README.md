Docker Environment for PHP Applications
-------------

This is a simple environment provided by Docker. It has been used with frameworks like **Laravel**.

**Enviroment**
- Nginx
- PHP 7.1
- MySQL
- Redis

**Get started**

Clone the this project and run *docker-compose up -d*. It will download the Docker images necessaries, and create the containers.

When Docker finishes the Nginx will be listening to the address http://app.dev:8888. So, you have to put the line *127.0.0.1 app.dev* in your */etc/hosts*.

Create a *index.html* or move your app files to the folder *web/app*.

**Nginx**

The application is hold on /var/www/html/app.dev. Docker has a mapped volume web/app to /var/www/html/app.dev. 
All you have to do is put your files on web/app - *this folder is ignored by git*.

**MySQL**

MySQL has two users root and dbuser both with the same password *123456*. It already has a database called *app*.
