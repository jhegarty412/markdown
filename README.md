# markdown



[Httpd docs on PHP-FPM](https://httpd.apache.org/docs/2.4/mod/mod_proxy_fcgi.html)

**ansible variables**
~~~~
apache_service_modules:
     - proxy
     - proxy_fcgi
     - proxy_http
~~~~ 
**package install**
~~~~
- name: PHP FPM Install
   yum:
       name: rh-php72-php-fpm
~~~~
**service**
~~~~
- name: Enable service
  systemd:
    name: rh-php72-php-fpm.service
    enabled: yes
    state: started
~~~~  

**httpd directives**
~~~~
<IfModule proxy_module>
ProxyPassMatch ^/(.*\.php)$ fcgi://127.0.0.1:9000/path/to/your/documentroot/$1
</IfModule>
~~~~

