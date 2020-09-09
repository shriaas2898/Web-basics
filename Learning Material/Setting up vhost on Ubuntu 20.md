# Setting up Virtual Host on Ubuntu 20 Apache2

## What is Virtual Host:
Virtual host is a mechanism to set up multiple hosts in a single system the user feels that they are getting redirected to different locations when in reality their requests are sent to the same IP, just on different directories. Every virtual host is identified by virtualname. Virtual are useful because you can utilize a single IP location and single machine to host multiple websites. Let’s see how we can setup virtual host on our own machine in few simple steps 

## Pre-requisites:
In order to setup vhost you need to install and configure **apache 2** on your ubuntu system. You can refer to [this](https://www.linuxbabe.com/ubuntu/install-lamp-stack-ubuntu-20-04-server-desktop) link to setup apache.

### Step 1: Intitalizing and configuring directory
The first step is to create directory which contains the website i.e the document root of your site.

create the folder for your website in `var/www/html`:
```bash
sudo mkdir /var/www/mysite
```
You need to have root priviliges to create a folder in  `var/www/html`

Now we need to change the permissions for `mysite` so that it can be accessed without root privilages. We will change the owner to current logged-in user to gain full access of `mysite` folder:
```bash
sudo chown $USER:$USER /var/www/mysite/
```
Where `$USER` contains name of current logged-in user.

Also we can ensure that `mysite` is readable by all the users:

```bash
sudo chmod 755 /var/www/mysite/
```

### Step 2: Creating demo page in `mysite`
Now that we are all done with setting up directory let's add some content to it.
**Note:** You can skip this step if you have website content ready with you.

Create a file in `mysite` using `nano
` or you can use any editor.
```bash
nano /var/www/mysite/index.html
```
Add some content like this:
```html
<html>
<title>My Site</title>
<body>
<h1>Hello and Welcome to My Site<h2>
This is where it all started......
</body>
</html>
```
Press `Ctrl+X` and save the file.

### Step 3: Creating configuration files for virtual host
We are all done with setting up content for our site. Let's move on to setup our virtual host file.

Apache provides a default file for virtual host called `000-default.conf` present in `/etc/apache2/sites-available/` which we can copy and modify a bit for our virtual host.
Let's copy the default file and open it in nano:
```bash
sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/mysite.local.conf

sudo nano /etc/apache2/sites-available/mysite.local.conf
```
You will see a bunch of parameters in this file. We will modify four of them for basic setup.
`SeverAdmin` -> the email of your website's admin
`Sever Name` -> the address of your website
`Document Root` -> the directory which contains the website.
`Server Alias` -> a sudo or virtual name that should be displayed on search bar while accessing the site.
```bash
<VirtualHost *:80>

        ServerName 127.0.0.2
        ServerAlias mysite.local
        ServerAdmin admin@mysite.com
        DocumentRoot /var/www/mysite

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```
Save the file and exit.

### Step 4: Enabling newly added virtual host
After configuring the virtual host file we have to enable it using `a2ensite` command (which rougly translates to apache2 enable site)
Change the directory and enable the site:
```bash
cd /etc/apache2/sites-available/
sudo a2ensite mysite.com.conf
```

To make the changes restart the apache server
```bash
sudo systemctl restart apache2
```

### Step 5: Configuring hosts file
The last step is to configure `/etc/hosts` file which contains list of IP addresses and names. It acts like a local DNS file.
Let's open the file using `nano`:
```bash
sudo nano /etc/hosts
```
Now add the IP address and name of the site.
**Note:** the name should be same as the name of file for virtual host i.e `mysite.local.conf`
```bash
127.0.0.1       localhost
127.0.0.2       mysite.local
```

And that's it!!

Open browser and type `http://mysite.local` and you can access your site.

Congratulations! you just setup a virtual host. 

### References:

https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-18-04-quickstart
https://linuxhint.com/install_apache_web_server_ubuntu/