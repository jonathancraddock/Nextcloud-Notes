# Nextcloud-Notes
Notes on some config changes while installing Nextcloud 22 on Ubuntu 20.04.

## Resources

* Hardening and Security Guidance -> https://docs.nextcloud.com/server/22/admin_manual/installation/harden_server.html  
* Computing For Geeks guide -> https://computingforgeeks.com/how-to-install-nextcloud-on-ubuntu-debian/  
* Nextcloud (Latest) -> https://nextcloud.com/install/#instructions-server  
* Cache Info -> https://docs.nextcloud.com/server/19/admin_manual/configuration_server/caching_configuration.html  
* SSL Check -> https://www.ssllabs.com/ssltest/  
* Nextcloud Security Check -> https://scan.nextcloud.com/  

### Let's Encrypt
```bash
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
sudo certbot --apache
```

### Strict Transport Security:
```bash
    <IfModule mod_headers.c>
      Header always set Strict-Transport-Security "max-age=15552000; includeSubDomains"
    </IfModule>
```
^- *added after server name, before directory block (note-* ***AFTER*** *setting up lets encrypt*

### Phone region:
```bash
sudo nano /srv/nextcloud/config/config.php

'default_phone_region' => 'GB',
```
^- *added phone region to end of file*

### Missing GMP
```bash
sudo apt install php-gmp
```

### Libmagickcore
```bash
sudo apt install libmagickcore-6.q16-6-extra
```

### Enable adding an SMB/CIFS share
```bash
sudo apt install smbclient
```
