# LAMP STACK IMPLEMENTATION PROJECT DOCUMENTATION

**LAMP**
: Is a Web technology stack who's  frameworks and tools are very specifically chosen to work together in creating a well-functioning software.

## **LAMP** is an acronymn for individual technologies (Linux, Apache, MySQL, PHP or Python, or Perl

* *Project steps*

1. installing apache and updating the firewall
2. installing mysql
3. installing php
4. creating a virtual host for your website using apache
5. enable php on the website

## **1.** *Installing apache and updating the firewall*

>`sudo apt update`

![packages update](.\images\packages-update.png)

>`sudo apt install apache2`

![apache2 install](./images/apache2-install.png)

>`sudo systemctl status apache2`

![apache2 status](./images/apache2-status.png)

>`curl http://localhost:80`
*#To access sever locally on the ubuntu shell.*

![apache2 server check](./images/apache-server.png)

>*#use server public IP/DNS to access server on the web.*
![apache2 server web](./images/server-web.png)

## **2.** *Installing mysql*

>`sudo apt install mysql`

![install mysql](./images/msql-installed.png)

>`sudo mysql`
>*#to connect to mysql as the administrative database root user*

![connect mysql](./images/connect-mysql.png)

>`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`
>*#To secure and set a password on mysql*

![secure mysql](./images/secure-mysql.png)

>`sudo mysql_secure_installtion`
>#*To start mysql interactive script*

![secure intaract](./images/secure-intaract.png)

>#*type Y(yes) to all required settings*

![mysql setting](./images/mysql-setting.png)

>`sudo mysql -p`
>*#To login to mysql using password*

`exit` *#To exit mysql console*

![testpw & exit](images/testpw-exit.png)

>`sudo apt install php libapache2-mod-php-mysql`
*To install php libapache2-mod-php-mysql packages all at once*

![php install](./images/php-install.png)

>*#installation successfull*

![php success](./images/php-sucess.png)

>`php -v` #*To confirm php version*

![php -v](./images/php-v.png)

## **4.** *creating a virtual host for your website using apache*

>`sudo mkdir /var/www/projectlamp`  
`sudo chown -R $USER:$USER ?var/www/projectlamp`  
`sudo vi /etc/apache2/sites-available/projectlamp.conf`

![php mkdir assing file owner config](./images/mkdir-own-config.png)

>`sudo vi /etc/apache2/sites-available/projectlamp.conf`

![vi-editor](./images/vi-editor.png)

>`sudo ls /etc/apache2/sites-available`  
`sudo a2ensite projectlamp`

![enable php site](./images/enabling-phpsite.png)

>`sudo a2dissite 000-default`

`sudo apache2ctl configtest`

`sudo systemctl reload apache2`

![ee](images/activate-new-phpconfig.png)

>`sudo echo 'HELLO LAMP from hostname' $|curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public ip' $(curl -s htp:/169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html`

![HTML text input](./images/index-html.png)

>*# Access the HTML page on the web, using the server public ip/DNS*

![HTML web output](./images/html-web-output.png)

## **5.** *enable php on the website*

>`sudo vim/etc/apache2/mods-enabled/dir.conf`

![rearrange index.php](./images/rearange-index.php.png)

>*# old file arrangement*

![old index file arrangment](images/old-index%20arrang.png)

>*# new file arrangement*

![new index file arrangement](images/new-index-arrange.png)

>`sudo systemctl reload apache2` *#reload apache so the changes take effect*

`vim /var/www/projectlamp/index.php` *#create a new file named index.php inside your custome web root folder*

![reload apache](images/reload-apache-nwfile.png)

>*#php file, to display php info*

![index.php info](images/vi-phpinfo.png)

>*#access php info web view using public IP/DNS*

![web view php info](./images/webview-php.png)

>`sudo rm /var/www/projectlamp/index.php`

>*#after checking the relevant information about your PHP server through the above page, it's best to remove the file you created as it contains sensitive information about your PHP environment and your ubuntu server*

![remove php file](images/rm-phpfile.png)