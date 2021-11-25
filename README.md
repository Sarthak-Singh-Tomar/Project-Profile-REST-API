# PROJECT PROFILE REST API

### Creating local development server:
We will create a local development server that can run and test our API as we build it. We are going to be creating a development server using a tool called Vagrant. Vagrant allows you to define the type of server you need for the project as a vagrant file and store this file with the source code of our project. You can create a new vagrant file by using the vagrant CLI tool.

> vagrant init ubuntu/bionic64

It initializes our project with a new vagrant file and it bases it on the ubuntu bionic 64 base image. These images are publicly available in the vagrant catalog box.

> vagrant up

what this will do is it will download the base image that we've specified in our vagrant file and then it will use VirtualBox to create a new virtual machine and then run our provisioning script when it starts the machine.

> vagrant ssh

once the vagrant box has been started we can then connect to the vagrant server by using the vagrant SSH command. Since our box is a completely different isolated box on our machine so it's a guest operating system, we need to connect to it using SSH.

> exit

To disconnect from the machine simply type exit and this will take you outside of the machine back onto your local machine.

#### when you connect to the machine and any command that you run in the terminal while you're connected to the machine will be ran on the guest operating system or the development server instead of your local machine.

### Synchronizing the development server with project directory:
For Synchronizing the development server with project directory you need to first connect to vagrant server. Once you connect to vagrant server type:

> cd /Vagrant

This will switch you to vagrant directory on our server. Now everything in this vagrant directory is synchronized with everything in our project folder. This synchronization works both ways from the server to our host and form our host to the server.

### Python virtual enviroment:
To create a python virtual environment go to the vagrant directory and use python venv command:

> python -m venv ~/env

using ~ will create python virtual environment in the home directory of the your vagrant server (which is not synchronized with local machine) opposed to the vagrant folder which is synchronized with our local machine. The way virtual environment works you need to activate and deactivate them. So when you're activated on a virtual environment all of the dependencies that you run in the python application will be pulled from the virtual environment instead of the base operating system. To activate virtual environment:

> source ~/env/bin/activate

To switch off from virtual environment type:

> deactivate

### Installing required packages:
To install the required packages which is django and djangorestframework for our project first create requirements.txt file
and then edit the file as follow:
django==<versio>
djangorestframework==<version>
save the file.

> touch requirements.txt

To install the requirements make sure that you are in vagrant directory and virtual environment is activated. Now type:

> pip install -r requirements.txt

-r stands for requirements.

### Creating Django project and application:
To create a django project we will use django command line tool - django-admin.

> django-admin.py startproject profiles_project .

To create a django application

> python manage.py startapp profiles_api

### Enabling the application:
You need to go to settings file for your django project and find "INSTALLED_APPS" block, this is where we need to list all of the apps that you need to use for your project. These are the following apps you need to add:

> 'rest_framework',
> 'rest_framework.authtoken',
> 'porfiles_api',

### Start Django development web server for testing:
You can start the django development server, first make sure you are using vagrant box and inside the vagrant directory and virtual enviroment is turned on. Now use:

> python manage.py runserver 0.0.0.0:8000

"python manage.py" It asks the django to start running development web server and this "0.0.0.0" means make it available on all network adapters on our development server and this ":8000" says start it in port 8000 so we can access it via port 8000. Now go to browser and type in search bar 127.0.0.1:8000 to check the that the server is up and running.
