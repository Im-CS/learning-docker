<h1>Drupal with Portgres in Docker</h1>

<h4>Create the docker-compose.yml file like this</h4>

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

<h4>Then run this command to start the container</h4>

```
docker-compose up -d
```


<h4>Watch demo here</h4>

[![WATCH DEMO HERE](https://i9.ytimg.com/vi/KYgojRVmCf0/hqdefault.jpg?sqp=CNiRq_oF&rs=AOn4CLBUd0HGF8wb1Q8ty4wt-JijRSFz4A)](https://youtu.be/KYgojRVmCf0)

