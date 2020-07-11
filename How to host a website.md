## How to host multiple websites on a single server using Apache HTTP Server
### Installation process of Apache Server (Run the following commands)
#### Step 1 :- Update System packages
> $ sudo apt update
#### Step 2 :- Install Apache Server
> $ sudo apt install apache2
#### Step 3 :- Start Apache Server
> $ sudo systemctl start apache2
### Create Dictonary for website
#### Step 4 :- Create folder 1
> $ sudo mkdir /var/www/html/project-management
#### Step 5 :- Create folder 2
> $ sudo mkdir /var/www/html/myportfolio_new
#### Step 6 :- Paste index.html and other dependent folders 1
> $ sudo cp -R /home/neeraj/my-projects/myportfolio_new/index.html /var/www/html/myportfolio_new
> $ sudo cp -R /home/neeraj/my-projects/myportfolio_new/resources /var/www/html/myportfolio_new
#### Step 7 :- Paste index.html and other dependent folders 2
> $ sudo cp -R /home/neeraj/my-projects/project-management/index.html /var/www/html/project-management
> $ sudo cp -R /home/neeraj/my-projects/project-management/resources /var/www/html/project-management
#### Step 8 :- Change the ownership of both websites to www-data
> $ chown -R www-data:www-data /var/www/html/project-management
> $ chown -R www-data:www-data /var/www/html/myportfolio_new
