#Centos 7 with nginx and php 5.6.

Any directory can be mapped into the container to /var/www as long as it contains your app and a conf.d directory containing any nginx vhosts config files.

For example, on the Host we might have these directories:

```
/var/www/conf.d/some-vhost.conf
/var/www/some-app/www
/var/www/some-app/logs
/var/www/certs/some-vhost.crt
/var/www/certs/some-vhost.key
```

```bash
docker run -d -p {hostsIp}:{hostsPort}:443 --name web -v /var/www/:/var/www -v /var/www/php.ini:/etc/php.ini "oodgaard/centos7-nginx-php56:latest"
```

Included PHP Modules:
bz2, calendar, Core, ctype, curl, date, dom, ereg, exif, fileinfo, filter, ftp, gettext, gmp, hash, iconv, json, libxml, memcache, mhash, mongo, openssl, pcntl, pcre, PDO, pdo_pgsql, pdo_sqlite, pgsql, Phar, posix, readline, Reflection, session, shmop, SimpleXML, soap, sockets, SPL, sqlite3, standard, sysvmsg, sysvsem, sysvshm, tokenizer, wddx, xdebug, xml, xmlreader, xmlwriter, xsl, yaml, Zend OPcache, zip, zlib

Zend Modules:
Xdebug, Zend OPcache
