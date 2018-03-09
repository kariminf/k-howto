# Set up Apache server on Ubuntu

## Install it

Install it (IT: the server, not the movie)

```sh
sudo apt-get install apache2
```

You may install PHP, MySQL and PHPMyAdmin as well

```sh
sudo apt-get install phpmyadmin
```

Don't worry! *phpmyadmin* depends on *php* and *php-mysql* packages.
So you don't have to write all these packages.

Then, test it by taping *127.0.0.1* on your navigator.
A page will appear, announcing that your server works just as it should be.
The page is located in **/var/www/html/**, so you should replace it.
When someone tape your IP address, this is what they get.

## Multiple local addresses

The default Ubuntu document root is **/var/www/html**

Let's say, I want to set up another address to a folder **/home/me/www/**:

* The folder is accessible locally from the address *127.0.0.2*
* It is accessible from outside from my IP address (obviously) and the port **8086**
(I wanted to use **8080**, but Apache Tomecat already took it. So, why not set up the last two digits from my birth-year)

Enter Apache2 configuration folder.
Create a new site configuration in **sites-available** (lets call it: **mySite**).
Then, mark it as enabled by making a link to it in **sites-enabled**.

```sh
cd /etc/apache2/
sudo touch sites-available/mySite.conf
sudo ln -s ../sites-available/mySite.conf sites-enabled/
```

Edit the newly created file, by entering this:

```aconf
Listen 8086

<VirtualHost 127.0.0.2  *:8086>

  #ServerName www.example.com

  ServerAdmin webmaster@localhost
  DocumentRoot /home/me/www/

  #You can set up another location for log files
  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```

Also, add this to **apache2.conf**

```aconf
<Directory /home/me/www/>
  Options Indexes FollowSymLinks
  AllowOverride None
  Require all granted
</Directory>
```

Then, restart apache2 server

```sh
sudo service apache2 restart
```

To access this website:

* Locally, you can access the website by taping *127.0.0.2*.
* From outside, suppose your IP address is *10.42.0.5* (a local network).
Then, others can access your website by taping *10.42.0.5:8086*.
