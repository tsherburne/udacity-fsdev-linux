## AWS Lightsail Hosting for: Wood Products Catalog
This respository is for project #6 (Linux Hosting) 
for the [Udacity Fullstack Developers Nano Degree](https://www.udacity.com/course/full-stack-web-developer-nanodegree--nd004).

This project is a clone of [project #4](https://github.com/tsherburne/udacity-fsdev-catalog) with some path name fixes to support the Apache hosting environment.

### Table of Contents

* [Lighsail Setup](#lightsail-setup)
* [Server Access](#server-access)

### Lightsail Setup
The following packages were installed on the Ubuntu [AWS Lightsail](https://aws.amazon.com/lightsail/) server:
```
sudo apt-get install apache2
sudo apt-get install libapache2-mod-wsgi

sudo apt install phthon-pip
sudo apt install sqlite
sudo pip install Flask
sudo pip install SQLAlchemy

sudo pip install google-api-python-client
sudo pip install google-auth
sudo pip install google-auth-oauthlib 
sudo pip install google-auth-httplib2
```
The apache server was configured to lauch the Python catalog application with the following:
```
/var/www/html/catalog.wsgi
```
```
import sys
sys.path.insert(0, '/home/ubuntu/website/udacity-fsdev-hosted-catalog/')

from server import app as application
```
```
/etc/apache2/sites-enabled/000-default.conf
```
```
WSGIDaemonProcess catalog user=ubuntu group=ubuntu threads=5
WSGIScriptAlias / /var/www/html/catalog.wsg
```

### Server Access
The URL for the catalog db application is:
```
http://ec2-52-1-33-79.compute-1.amazonaws.com/
```
SSH is enabled on port 2200 for the 'grader' user


