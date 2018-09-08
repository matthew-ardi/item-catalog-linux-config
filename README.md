# item catalog linux configuration

Application deployed by this configuration can be found here: [item-catalog](https://github.com/matthew-ardi/item-catalog)

IP address: 13.58.78.114

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

    WSGIDaemonProcess ...
    ...
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

> note that the application is currently deployed using Flask web server deployment due to issues regarding permissions. Changes will be made and this documentation will be updated.
