<!--
N.B.: This README was automatically generated by https://github.com/YunoHost/apps/tree/master/tools/README-generator
It shall NOT be edited by hand.
-->

# Calibre-web for YunoHost

[![Integration level](https://dash.yunohost.org/integration/calibreweb.svg)](https://dash.yunohost.org/appci/app/calibreweb) ![](https://ci-apps.yunohost.org/ci/badges/calibreweb.status.svg) ![](https://ci-apps.yunohost.org/ci/badges/calibreweb.maintain.svg)  
[![Install Calibre-web with YunoHost](https://install-app.yunohost.org/install-with-yunohost.svg)](https://install-app.yunohost.org/?app=calibreweb)

*[Lire ce readme en français.](./README_fr.md)*

> *This package allows you to install Calibre-web quickly and simply on a YunoHost server.
If you don't have YunoHost, please consult [the guide](https://yunohost.org/#/install) to learn how to install it.*

## Overview

Browsing, reading and downloading eBooks using a Calibre database

**Shipped version:** 0.6.14



## Screenshots

![](./doc/screenshots/screenshot.png)

## Disclaimers / important information


### Post install

Users having the calibreweb.main authorization group can be automatically sync from within the app, by using the "Import LDAP user" function.
Deletion of a Yunohost User will delete the according calibreweb-user.


### Library management

* **Library** will be placed in `/home/yunohost.multimedia/share/eBook` folder except if both :
  - calibreweb is set as a private application
  - calibreweb library is set as a public library

In this case the library will be set in `/home/yunohost.multimedia/[admin]/eBook` folder. Library folder can always be changed manually in the application settings by the administrator.

* By default, Yunohost backup process **will backup** Calibreweb library.
You may deactivate backup of the library with 
```
yunohost app setting calibreweb do_not_backup_data -v 1
```

* By default, removing the app will **never** delete the library.


* Authorization access to library to be done manually after install if Calibre library was already existing (except in yunohost.multimedia directory), for example :
```
chown -R calibreweb: path/to/library
or
chmod o+rw path/to/library
``` 

### OPDS

For **OPDS** to work, most OPDS-readers will require the app must be set in public mode.
Also, you may have to activate the "anonym browsing" for some reader to access book covers or download books ([source](https://github.com/janeczku/calibre-web/wiki/FAQ#which-opds-readers-work-with-calibre-web)).

### Versionning

Version number in Yunohost is different from the upstream Calibre-web app : version 0.X.Y becomes 0.9.X.Y in Yunohost. This is due to the fact that Calibre-web was not versionned when first packages were built.

### Known Limitations

* Do not use a Nextcloud folder. It's all right if the folder is an external storage in Nextcloud but not if it's an internal one : Changing the data in the library will cause trouble with the sync
* "Magic link feature is not yet available
* Change to library made outside Calibreweb are not automatically updated in Calibreweb. It is required to disconnect and reconnect to see the changes : Do not open a database both in Calibre & Calibreweb!
* Kobo Sync doesn’t work when Calibreweb is installed on a subdomain. This issue is caused by nginx. However, it works great when installed on a path e.g. `https://domain.tld/calibreweb`

### Todo
- [ ] Update mail settings with yunohost settings
- [ ] enable magic link
- [ ] Add cronjob to reload database (for nextcloud integration)
- [ ] Add config-panel option to trigger do_not_backup_data
- [ ] Add config-panel to manage max upload size
- [ ] Add action to restart the server
- [ ] Add action to synchronize users
- [ ] Add action to deactivate LDAP et retrieve admin password
- [ ] Use internal updater to update version?

## Documentation and resources

* Official admin documentation: https://github.com/janeczku/calibre-web/wiki
* Upstream app code repository: https://github.com/janeczku/calibre-web
* YunoHost documentation for this app: https://yunohost.org/app_calibreweb
* Report a bug: https://github.com/YunoHost-Apps/calibreweb_ynh/issues

## Developer info

Please send your pull request to the [testing branch](https://github.com/YunoHost-Apps/calibreweb_ynh/tree/testing).

To try the testing branch, please proceed like that.
```
sudo yunohost app install https://github.com/YunoHost-Apps/calibreweb_ynh/tree/testing --debug
or
sudo yunohost app upgrade calibreweb -u https://github.com/YunoHost-Apps/calibreweb_ynh/tree/testing --debug
```

**More info regarding app packaging:** https://yunohost.org/packaging_apps