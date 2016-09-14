#Wordpress install
##Project notes/requirements
For this wordpress install I had the following requirements:
-SSL/TLS secure connection (using nginx reverse proxy and let's encrypt nginx proxy companion
-local persist driver used for data safety and facilitating backups
-Separate containers for Wordpress, Database and Redis
-Redis for performance/caching
-only wordpress container exposed to the reverse proxy, other containers on a back-end network

##My post install notes
###uploads.ini
Copy uploads.ini to appropriate file in local persist directory structure.

###SSL
Settings>General add https urls
in wp-config.php
define('FORCE_SSL_ADMIN', true);

###Redis
define('WP_REDIS_HOST', 'redis');

install redis-cache wp plugin

###Multisite
https://codex.wordpress.org/Create_A_Network

###Add nginx rproxy to my-path-front network
docker network connect your-network-name nginx-proxy

<!--TODO: uploads settings, install commons, pick redis plugin-->

