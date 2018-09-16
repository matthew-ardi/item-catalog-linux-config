# item catalog linux configuration

Application deployed by this configuration can be found here: [item-catalog](https://github.com/matthew-ardi/item-catalog)

IP address: 35.171.188.216

Domain name : [mardiapp.tk/dashboard](http://www.mardiapp.tk/dashboard/)

## Installed Dependencies
- Apache2
- Python 2.7
- Virtualenv

## Configuration Details
Application can be found under
```
/var/www/item-catalog
```
within the application above, a ```app.wsgi``` was made to deploy the application as WSGI app.

Further configuration of Apache can be found in
```
/etc/apache2/sites-available
```
This application was configured for apache2 under the ```web.conf``` configuration.

```web.conf``` file should be similar to the following:

```
<VirtualHost *:80>
    ServerName www.mardiapp.tk
    ServerAdmin admin@mardiapp.tk

    WSGIDaemonProcess mardiapp.tk python-path=/var/www python-home=/var/www/item-catalog/venv
    WSGIScriptAlias / /var/www/item-catalog/app.wsgi

    <Directory /var/www/item-catalog>
        Order allow,deny
        Allow from all
    </Directory>

    Alias /static /var/www/item-catalog/templates

    <Directory /var/www/item-catalog/templates>
        Order allow,deny
        Allow from all
    </Directory>

    <Directory /var/www/.python-eggs>
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    LogLevel warn
    CustomLog ${APACHE_LOG_DIR}/access.log combined

   </VirtualHost>
```

## Locating SSH key for user
to locate ssh key for each user, go to the following path,
```
/home/<user name>/.ssh/authorized_keys
```

for example
```
/home/grader/.ssh/authorized_keys
```

## List of Third Party Resources

Technical:
- [Flask_SQLalchemy extension](http://flask-sqlalchemy.pocoo.org/2.3/) used as helper for SQLalchemy operations.
- [Google APIs](https://developers.google.com/products/)
- [Google Oauth2client - deprecated](https://github.com/google/oauth2client)

References:
- [https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps) used as a reference to test apache2 server. sample programs could be found in the same server under ```/var/www/FlaskApps``` with the apache2 configuration in ```/etc/apache2/sites-available/FlaskApp.conf```. The application is named as FlaskApp.



> note that the application is currently deployed using Flask web server deployment due to issues regarding permissions. Changes will be made and this documentation will be updated.
