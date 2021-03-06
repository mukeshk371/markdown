## _How Does a website Work?_
![DNS](https://www.thesslstore.com/blog/wp-content/uploads/2019/04/DNS-Diagram.png "dns")
## _Importan terms for hosting a website_
| Terms | Description |
| :---- | ----------- |
| IP Address | Every computer has their own unique address assined on the internet which is known as **_IP Address (Internet Protocol)_**. <br> _Example: 198.128.289.1_ |
| DNS Server | DNS Server is a computer server. It contains a database having IP address and their associated hostname |
## _Importan terms descriptions_
| Domain Name System (DNS)     |
| ---------- |
|  When users access a web page then they don't type that ip address. They type like _www.google.com_. A web address with a hostname in it. <br> The way through which a web address get translated into an ip address is known as _**Domain Name System (DNS)**_.<br><br> Its very tough to remember ip addresses of all websites. Computer remembers the ip address and DNS converts a **_URL (Uniform Resource Locator)_** into IP Address that computer can understand.<br><br> When we type a url like(google.com) in the browser. Then, the browser needs the ip address of google.com. Then, the browser contact to the DNS server to query the location of the server where the webpages are stored.    |
## _Web Hosting_
![DNS](https://www.website.com/img/skin/what_is_web_hosting.webp "dns")
## _How to host multiple websites on a single server using Apache HTTP Server_
### Installation process of Apache Server (Run the following commands)
#### Step 1 : Update System packages
> $ sudo apt update
#### Step 2 : Install Apache Server
> $ sudo apt install apache2
#### Step 3 : Start Apache Server
> $ sudo systemctl start apache2
### _Create Dictonary for website_
#### Step 4 : Create folder 1
> $ sudo mkdir /var/www/html/project-management
#### Step 5 : Create folder 2
> $ sudo mkdir /var/www/html/myportfolio_new
#### Step 6 : Paste index.html and other dependent folders 1
> $ sudo cp -R /home/neeraj/my-projects/myportfolio_new/index.html /var/www/html/myportfolio
>
> $ sudo cp -R /home/neeraj/my-projects/myportfolio_new/resources /var/www/html/myportfolio
#### Step 7 : Paste index.html and other dependent folders 2
> $ sudo cp -R /home/neeraj/my-projects/project-management/index.html /var/www/html/project-management
>
> $ sudo cp -R /home/neeraj/my-projects/project-management/resources /var/www/html/project-management
#### Step 8 : Change the ownership of both websites to www-data
> $ sudo chown -R www-data:www-data /var/www/html/project-management
>
> $ sudo chown -R www-data:www-data /var/www/html/myportfolio_new
#### Step 9 : Create Apache virtual host configuration file for folder/website 1
> $ sudo nano /etc/apache2/sites-available/project-management.conf
#### Step 10 : Paste the following to the project-management.conf
> &#60;VirtualHost *:80&#62;<br/>
ServerAdmin admin@localhost<br/>
ServerName  project-management<br/>
DocumentRoot /var/www/html/project-management<br/>
DirectoryIndex index.html<br/>
ErrorLog ${APACHE_LOG_DIR}/192.168.0.101_error.log<br/>
CustomLog ${APACHE_LOG_DIR}/192.168.0.101_access.log combined<br/>
&#60;/VirtualHost&#62;
#### Step 11 : Paste the following to the myportfolio.conf
> &#60;VirtualHost *:80&#62;<br/>
ServerAdmin admin@localhost<br/>
ServerName  myportfolio<br/>
DocumentRoot /var/www/html/myportfolio_new<br/>
DirectoryIndex index.html<br/>
ErrorLog ${APACHE_LOG_DIR}/192.168.0.101_error.log<br/>
CustomLog ${APACHE_LOG_DIR}/192.168.0.101_access.log combined<br/>
&#60;/VirtualHost&#62;
#### Step 12 : Enable both virtual hosts
> $ sudo a2ensite myportfolio_new
>
> $ sudo a2ensite project-management
#### Step 13 : Retart Apache Server
> $ sudo systemctl restart apache2
#### Step 14 : Now check both the websites using following urls
[Website 1](http://192.168.31.14/project-management)
[Website 2](http://192.168.31.14/myportfolio)
