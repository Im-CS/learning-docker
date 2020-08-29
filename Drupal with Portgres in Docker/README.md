#Drupal with Portgres in Docker

##Create the docker-compose.yml file like this

```
  1 version: '2'
  2 
  3 services:
  4 
  5   drupal:
  6     image: drupal:8.8.2
  7     ports:
  8       - 8080:80
  9     volumes:
 10       - web-modules:/var/www/html/modules
 11       - web-profiles:/var/www/html/profiles
 12       - web-themes:/var/www/html/themes
 13       - web-sites:/var/www/html/sites
 14 
 15   postgres:
 16     image: postgres:12.1
 17     environment:
 18       POSTGRES_PASSWORD: admin
 19     volumes:
 20       - web-data:/var/lib/postgresql/data
 21 
 22 volumes:
 23   web-data:
 24   web-modules:
 25   web-profiles:
 26   web-themes:
 27   web-sites:
```

##Then run this to start the comntainer
```
docker-compose up -d
```

##Watch demo here
!["WATCH DEMO HERE" (https://img.youtube.com/vi/https://youtu.be/KYgojRVmCf0/0.jpg)]
(https://youtu.be/KYgojRVmCf0 "Watch demo here")
