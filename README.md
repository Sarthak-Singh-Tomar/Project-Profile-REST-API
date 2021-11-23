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
