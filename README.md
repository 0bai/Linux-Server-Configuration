# Linux Server Configuration

This project consists of setting up Linux server with good security settings, running web server, and deployment of the Item Catalog project from earlier in the ND.

## Initializing the server

I have created an Ubuntu 16.04 server, using Google's Compute Engine service. the server is running on us-east1-b zone. the server's external ip is : [35.243.167.3](35.243.167.3.xip.io)

## Updating the server

You can update the server using the following commands
```
sudo apt-get update
sudo apt-get upgrade
```

## Creating Grader User

I have created the Grader user using
```
sudo adduser grader
```
I have added the user to sudoers.d, then created keys using:
```
ssh-keygen
```
Then added the public key to .ssh directory in Grader's home directory and edited the directory's permissions.

## Setting firewall rules

First we need to block all incoming connections:

```
sudo ufw default deny incoming
```

After that we need to allow outgoing connections :
```
sudo ufw default allow outgoing
```
Then we only allow ports 2200, 123, and 80:
```
sudo ufw allow 2200/tcp
sudo ufw allow www
sudo ufw allow ntp
```
We also need to enable the firewall
```
sudo ufw enable
```
And we can check the status using
```
sudo ufw status
```

## Installing and configuring the Items Catalog application
I have [this](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps) tutorial for Installing the app using Apache & mod_wsgi.
## Built With
* [python3](https://www.python.org/download/releases/3.0/) Python is an open soure and easy to learn programming language.
* [pip3](https://pip.pypa.io/en/stable/) - Dependency Management.
* [flask](http://flask.pocoo.org) - Flask is a microframework for Python based on Werkzeug and Jinja 2.
* [OAuth2](https://oauth.net/2/) - OAuth 2.0 is the industry-standard protocol for authorization.
* [sqlalchemy](https://www.sqlalchemy.org) - SQLAlchemy is the Python SQL toolkit and Object Relational Mapper that gives application developers the full power and flexibility of SQL.
* [git](https://git-scm.com) - Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.
* [mod wsgi](https://modwsgi.readthedocs.io/en/develop/#) - The mod_wsgi package implements a simple to use Apache module which can host any Python web application.
* [xip.io](http://xip.io) - xip.io is a magic domain name that provides wildcard DNS
for any IP address.

# Appendix: Access Details
>IP address: 35.243.167.3 | SSH port: 2200 | URL: http://35.243.167.3.xip.io | SSH user : grader | SSH Key: Submitted in the comments section | App directory: /var/www/html/ItemsCatalog

## Authors

* **Obai Alnajjar** - *Initial work* - [0bai](https://github.com/0bai)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Udacity Full Stack Nano Degree Team
