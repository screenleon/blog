# Nginx
> **Lien Chen** *2020-12-03*

* Nginx using php need `unix:/var/run/php/php[VERSION]-fpm.sock`
  * Start run service `php[version]-fpm`, it will generate *.sock file at /var/run/php.
  * You might meet error that `NGINX: connect() to unix:/var/run/php7.2-fpm.sock failed (2: No such file or directory)`
    * Edit `/etc/php/[VERSION]/fpm/pool.d/www.conf`

Follow instructor
```
listen.owner=nobody
 
listen.group=nobody
```

Turn to 
```
listen.owner=nginx
 
listen.group=nginx
```
To make sure nginx have permission to exec it.

[reference1](https://blog.csdn.net/chesterblue/article/details/100081797)
[reference2](https://stackoverflow.com/questions/51158830/nginx-connect-to-unix-var-run-php7-2-fpm-sock-failed-2-no-such-file-or-dir)