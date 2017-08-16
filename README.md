# Udacity's fsnd Linux Server Configuration!  

## Description  
App URL: http://37.59.103.242/  
Software used: apache2, mod_wsgi, flask, postgresql  

## Configuration  
#### Apache2:  

- Run the app's apache2 process as the new user.
- Changed pickyapp logs to be saved in the project's `logs` directory under the new user's home.
- Disabled Etag (in `apache2.conf`).  
- Enabled caching of static files.  

#### Flask app:  

- Added the `main.wsgi` file.  
- Edited the `run.py` file so that the app instance is created relative to the `PICKY_SETTINGS` env var.  
- Added an `activate_this.py` to be used by the wsgi file to active the virtual environment.  

#### Postgresql:  
- Just a regular postgres install (install, create role matching the user who's running the app, create databases).  

#### Logrotate:  
- Compress and to keep only 1 week worth of backlogs if logs don't accumulate over 100MB of size.  
- Pickyapp logs will be emailed to me when a rotation happens, the config is there, i just need a domain name and some more setup (irrelevant to this project, just wanted to experiment), gmail rejects the emails now since they have attachments, it's not a postfix problem since regular emails get delivered, https://support.google.com/mail/answer/81126#authentication.  

#### Postfix:  
- Changed recipient to my email.
- Changed `mailbox_size_limit`.
- added a logrotate entry for the mail logs.

## reference:
#### WSGI:  
http://flask.pocoo.org/docs/0.12/deploying/mod_wsgi/  
https://github.com/pypa/virtualenv/blob/master/virtualenv_embedded/activate_this.py  
#### postgres:  
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04  
#### logrotate:
https://support.rackspace.com/how-to/understanding-logrotate-utility/  
#### postfix:  
https://www.cyberciti.biz/tips/postfix-mail-server-limit-the-mailbox-size.html  
