# wp-build #
Code based on https://v4-alpha.getbootstrap.com/examples/narrow-jumbotron/

1. Open your wp-build project in C9.io...__DO NOT START THE SERVER__
2. Delete all local files and folders __EXCEPT__ the ```.c9``` folder. 
3. Then Copy and paste each of these ONE LINE AT A TIME in your bash terminal:
```sh
git init
git remote add mrc git@github.com:zeromile/wp-build.git
git pull mrc master
git remote rm mrc
git remote add origin git@github.com:USERNAME/wp-build.git   <--- COPY THIS FROM YOUR REPO, YO
git checkout -b monday
```

4. Update your PHP version and install some extra stuff we'll need. Copy and paste each of these ONE LINE AT A TIME:
```sh
sudo add-apt-repository ppa:ondrej/php -y
sudo apt-get update -y
sudo apt-get install php7.0-curl php7.0-cli php7.0-dev php7.0-gd php7.0-intl php7.0-mcrypt php7.0-json php7.0-mysql php7.0-opcache php7.0-bcmath php7.0-mbstring php7.0-soap php7.0-xml php7.0-zip -y
sudo mv /etc/apache2/envvars /etc/apache2/envvars.bak
sudo apt-get remove libapache2-mod-php5 -y
sudo apt-get install libapache2-mod-php7.0 -y
sudo cp /etc/apache2/envvars.bak /etc/apache2/envvars
sudo restart service apache2
```

5. Grab a newer (not the latest) version of WordPress by copying and pasting this into bash:
```sh
curl -O https://wordpress.org/wordpress-4.8.9.zip
```

6. Unzip the WordPress package and then delete the zip file by copying and pasting each line into bash:
```sh
unzip wordpress-4.8.9.zip
rm wordpress-4.8.9.zip
```

7. Install PHPMyAdmin package by copying and pasting this into bash:
```sh
phpmyadmin-ctl install
```

8. Open up the Wordpress folder in the file manager and rename the file called ```wp-config-sample.php``` to ```wp-config.php```
9. Open up the wp-config file and replace lines 22-32 with these lines: (copy and paste)
```
/** The name of the database for WordPress */
define('DB_NAME', 'c9');

/** MySQL database username */
define('DB_USER', substr(getenv('C9_USER'), 0, 16));

/** MySQL database password */
define('DB_PASSWORD', '');

/** MySQL hostname */
define('DB_HOST', getenv('IP'));
```

10. Pull in the template file we will be using by copying and pasting this into bash:
```sh
curl -LOk https://github.com/html5blank/html5blank/archive/stable.zip
```

11. Upack the zip file and then delete it by copying and pasting each line into bash:
```sh
unzip stable.zip -d wordpress/wp-content/themes
rm stable.zip
```
12. Start your server and click the link to visit. Add ```/wordpress``` at the end url to begin installation...like this:
```sh
https://wp-build-zeromile.c9users.io/wordpress
```
13. Follow the remaining install instructions until you are inside your new WordPress dashboard
14. Go to Appearance->Themes and activate the HTML5 Blank theme
15. Remove the other themes by returning to the bash window and copying and pasting this line:
```sh
rm -r wordpress/wp-content/themes/twenty*
```