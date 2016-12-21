# Linux Server Configuration

This document describes the configuration made to a linux server so it can be ready to secure serve a web application.

### Server location and access

The server has the `35.161.11.171` IP address asing, and remote users can login thought ssh at port `2200`.

### URL of hosted application 

The catalog web app can be access at [`http://35.161.11.171/`](http://35.161.11.171/).

### List of software installed 

#### Ubuntu packages 

- libpam-cracklib
- apache2
- libapache2-mod-wsgi
- postgresql
- libpq-dev
- git
- python-pip 
- python-dev

Also all repositories and currently installed packages was updated.

#### Python packages

- Flask
- Flask-RESTful
- Flask-SQLAlchemy
- Flask-SeaSurf
- Jinja2
- MarkupSafe
- SQLAlchemy
- Werkzeug
- aniso8601
- argparse
- httplib2
- itsdangerous
- oauth2client
- pyasn1
- pyasn1-modules
- python-dateutil
- python-simplexml
- pytz
- requests
- rsa
- six
- wsgiref
- psycopg2

### Configurations made to the server

1.  It was created a new user called "grader" and added to the sudoers user group, the user also was given ssh access with its correspondent rsa key.
1.  The ssh port was canged to 2200 and blocked the root remote login.
1.  The module libpam-cracklib was installed an configured to require users to have a strong password.
1.  The local timezone was changed to UTC.
1.  The Uncomplicated Firewall UFW got the folowing allow tcp rules on ssh(2200), www(80) and ntp(123). A default deny incoming and allow outgoing communication policy was also added. 
1.  The apache server and its wsgi module got configured to serve the Python-flask catalog web app.
1.  The catalog app was configured to use postgresql as database managent system and the psycopg2 driver with all its dependecies got installed too.
1.  The catalog relational schema was loaded to the postgresql DB along with some initial fixtures.

### References 

- [PAM module manual](https://linux.die.net/man/8/pam_cracklib)
- [Ubuntu Time Management](https://help.ubuntu.com/community/UbuntuTime)
- [SQLAlchemy Engine Configuration](http://docs.sqlalchemy.org/en/latest/core/engines.html)
