# Help-Desk-Ticketing-Lab
## Introduction
This lab consists of a VM (debian) that is cofigured as an apache web server, with MariaDB as the main database storage, and hosting osTicket. With these, I am able to simulate an enterprise level ticketing system to grasp the fundemental process behind ticketing and resolving problems. This lab, once completed, will act as a way for me to simulate technical problems and practice resolving them. The following portion are the steps I took to configure said lab. Anyone is free to read over and use it to get help with setting up this type of lab.
## Installation Steps
Installing **osTicket** has prerequisites that must be met. The following are the steps that I underwent during installation.
1. Created a VM that will host osTicket. Since osTicket isn’t demanding much hardware, I opted to use **debian** as the OS.
2. Now within the VM, Apache webserver (w/ URL Rewrite module) PHP 8.2 - 8.4, and MySQL 5.5 (mariaDB) must be installed.

### The following is installing the Apache webserver
3. Once logged into the VM, go to the terminal and enter the following:

     `sudo apt install apache2`
   
     `sudo services apache2 start`
4. With apache installed, to view its status use the following:

    `sudo systemctl status apache2`
  
5. The following can be used to stop and restart the server:
   
    `apachectl -k stop`
  
    `Apachectl -k graceful`
   
### The following is installing PHP
6. Once logged into the VM, go to the terminal and enter the following:

    `sudo apt update`
   
    `sudo apt install -y php`
   
7. PHP has now been installed successfully!

### The following is installing MariaDB
8. Once logged into the VM, go to the terminal and enter the following:

    `sudo apt update`

    `sudo apt install mariadb-server`

    `sudo mariadb-secure-installation`

    `sudo systemctl start mariadb `

### Creating a database, user, password, hostname
9. Within the terminal of the web server enter the following to connect to MariaDB:

    `mariadb -u root -p -h localhost`
   
10. Created a database with the following:

    `CREATE DATABASE ticketLab;`

11. Next is creating a user, password and hostname:

    `CREATE USER ‘username’@’hostname’ IDENTIFIED BY ‘password’;`
    
13. If necessary, next is to grant the necessary privileges to the newly created user for database access. Utilize the `GRANT` to do so. In my case I used the `GRANT ALL PRIVILEGES` command since it will be hosted locally.

### Configuring the Apache HTTP Server
14. At this point, it is crucial to download the appropriate osTicket downloadable folder from the website onto the VM. Do so from here: https://osticket.com/download/ 
15. Critical to test the apache webserver connection. Do so by entering the following into the web browser:
    
    `http://*IP_address_of_VM* `
    
      If successful, it should be greeted with the apache default page.
    
17. The apache installation created the following path: */var/www/html/*. Within this path, the folder that was downloaded from osTicket needs to be moved here.
    
    Should result in the path: */var/www/html/foldername/upload*

    Next, it is recommended to remove *index.html*

    With these steps, should be greeted with the *foldername* index. 

18. Instead of the debian default page, it should be met with the osTicket installation.
19. The installer will mention any missing extensions, recommended to install only those that are needed.
20. Going through the installer, a page will be reached regarding: System Settings, Admin User, and Database Settings. Enter the information accordingly (for admin and database entries, enter the information that was created in previous steps.
21. If successful, should be greeted with a page that explains it was a success. The page includes two crucial links for accessing osTicket as a client and staff.
  
    Ensure to save those URLs.

#### With this, osTicket should be operational and available to test/play around with.















