# Linux__openstack
Installation steps

## Ubuntu

### Dashboard

First install keystone following these steps
https://docs.openstack.org/keystone/latest/install/keystone-install-ubuntu.html

Then install the dashboard following these steps
https://docs.openstack.org/horizon/latest/install/install-ubuntu.html

_note: Do the access using the host ip instead of controller (ex: http://192.168.10.15/horizon)_

If there's some error, see apache log with this command:

```
tail /var/log/apache2/error.log -f
```

It will probably be necessary to install ubuntu-theme package:

```
apt install openstack-dashboard-ubuntu-theme
```


If occours this error:

```
sqlalchemy.exc.ProgrammingError: (pymysql.err.ProgrammingError) (1146, "Table 'keystone.project' doesn't exist"
```

Do:

```
keystone-manage db_sync
```
