# Linux__openstack
Installation steps


## Ubuntu

### Install openstack

```
add-apt-repository cloud-archive:xena
apt install nova-compute
apt install python3-openstackclient
```

### Dashboard

First install keystone following these steps
https://docs.openstack.org/keystone/latest/install/keystone-install-ubuntu.html

Then install the dashboard following these steps
https://docs.openstack.org/horizon/latest/install/install-ubuntu.html

_notes:_
  1. Use the server ip instead of controller in the configuration (ex: 192.168.10.15);
  1. Do the access using the host ip instead of controller (ex: http://192.168.10.15/horizon)

<br>

#### How to see the logs

If there's some error, see apache log with this command:

```
tail /var/log/apache2/error.log -f
```

Or the keystone log:

```
tail /var/log/apache2/keystone.log -f
```

<br>

#### Possible errors

It will probably be necessary to install ubuntu-theme package:

```
apt install openstack-dashboard-ubuntu-theme
```

<hr>


If you can't connect to mysql database, see _bind-address_ in /etc/mysql/mariadb.conf.d/50-server.cnf, and set it to this:

```
bind-address            = 0.0.0.0
```

<hr>

If occours this error:

```
sqlalchemy.exc.ProgrammingError: (pymysql.err.ProgrammingError) (1146, "Table 'keystone.project' doesn't exist"
```

Do:

```
keystone-manage db_sync
```
