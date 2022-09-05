---
description: Quick overview of how to install this cute cat.
---

# Installation

_This guide was created for Servers that support the .htaccess file. I cannot guarantee that it will work on servers that don't._

### Installing from GitHub

First, you need to clone the latest version of the software to the place you want it.

```shell
git clone https://github.com/H33Tx/KuroNeko/releases/latest /var/www/yoursite.com
```

After that, go into the folder.

```shell
cd /var/www/yoursite.com
```

### Preparing the MySQL Database

Before setting up the config-file properly, you need to import the .sql file to a MySQL Database. You can do this either with phpMyAdmin (which I highly recommend) or through the command-line.

{% tabs %}
{% tab title="phpMyAdmin" %}
1. Login to phpMyAdmin
2. Create new Database
3. Import `kuroneko.sql`
4. Done
{% endtab %}

{% tab title="Command-line" %}
```shell
# Login to MySQL Database
mysql -u username -p password
# Then create database and replace 'database_name' with the name of your choice
mysql> CREATE DATABASE database_name;
# Then press CTRL+D to exit the MySQL DB
# For the next step, make sure you are still in the folder
mysql -u username -p password database_name < kuroneko.sql
# You should be done if there are not any errors :)
```
{% endtab %}
{% endtabs %}

### Setting up the config-file

After creating the Database, you are ready to setup the config-file.

```shell
nano config.php
```

There you can customize all the stuff. Here's a quick overview of what does what:

* `$config["title"] (string)` The title of the site
* `$config["slogan"] (string)` The slogan of the site
* `$config["domain"] (string)` The domain without https://www and without sub folder and slashes
* `$config["url"] (string)` The complete URL to the page with https:// and ending with a slash
* `$config["cache"] (bool)` Enable or disable Caching
* `$confg["cachetime"] (int)` The amount of seconds before the page is cached again (default: 1 month)
* `$config["signup"] (bool)` Enable or disable registrations
* `$config["private"] (bool)` Force users to login
* `$config["cookie"] (string)` The cookie-prefix to store login-sessions
* `$config["perpage"] (int)` The default amount of items shown on a page
* `$min_un_length (int)` The amount of chars the username needs at least
* `$max_un_length (int)` The amount of chars the username can have at most
* `$min_pw_length (int)` The amount of chars the password needs at least
* `$max_pw_length (int)` The amount of chars the password can have at most
* `$min_em_length (int)` The amount of chars the Email needs at least
* `$max_em_length (int)` The amount of chars the Email can have at most
* `$images["signup"] (string)` The image that will be shown on the left side of the Signup-container
* `$images["login"] (string)` The image that will be shown on the left side of the Login-container
* `$images["avatar"] (string)` The image that will be the default avatar for new users
* `$images["footer_bg"] (string)` The background-image of the footer
* `$images["loading"] (string)` The image, that will be shown when an image is still loading
* `$slave["host"] (string)` The MySQL Database host
* `$slave["user"] (string)` The username for the MySQL Database
* `$slave["pass"] (string)` The password for the user
* `$slave["tale"] (string)` The name of the MySQL Database

### Creating an Admin

After you are done with setting up the MySQL Database and the config-file, visit your site and go to the signup-page and create an account there. When you are done, you should be redirected to the login-page. Login and check if everything worked fine.

If yes, you need to set the user-level in the DB to `9001`.

{% tabs %}
{% tab title="phpMyAdmin" %}
1. Login to phpMyAdmin
2. Select the Database and go to the table `users`
3. Set the level of yourself to `9001`
4. Done
{% endtab %}

{% tab title="Command-line" %}
{% code overflow="wrap" %}
```shell
# Login to MySQL Database
mysql -u username -p password
# Then update the account and set the level to 9001
# Make sure to replace 'database_name' with the name of yours
mysql> UPDATE database_name.users SET level=9001
# If it asks for any confirmation, just confirm
# If everything went right, you are done here :)
```
{% endcode %}
{% endtab %}
{% endtabs %}

#### Command-line

### Post-setup

Now that you are done with installing, your instance of KuroNeko is ready to be used. To customize it, read the Advanced section.

If you encountered any errors, bugs or anything like that and don't know how to fix them after doing some research, consider joining the Discord so I can assist you. The link can be found in the header.

