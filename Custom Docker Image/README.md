# Drupal with Portgres in Docker

## Create the dockerfile like this

```
FROM drupal:8
RUN apt-get update && apt-get install -y git && rm -rf /var/lib/apt/lists/*
WORKDIR ~/var/www/html/themes
RUN git clone --branch 8.x-3.x --single-branch --depth 1 https://git.drupal.org/project/bootstrap.git && chown -R www-data:www-data bootstrap
WORKDIR ~/custom-drupal
```

## Create the docker-compose.yml file like this

```
version: '2'

services:

  drupal:
    build: .
    ports:
      - 8080:80
    volumes:
      - web-modules:/var/www/html/modules
      - web-profiles:/var/www/html/profiles
      - web-themes:/var/www/html/themes
      - web-sites:/var/www/html/sites

  postgres:
    image: postgres:12.1
    environment:
      POSTGRES_PASSWORD: admin
    volumes:
      - web-data:/var/lib/postgresql/data

volumes:
  web-data:
  web-modules:
  web-profiles:
  web-themes:
  web-sites:

```

## Then run this command to start the container
```
$ docker-compose up -d
```

## To login
```
$ docker login -u <dockerhub username>
```

##### Example
```
$ docker login -u iamcs
```

## To commit image
```
$ docker commit <container name> <repo name>
```

##### Example
```
$ docker commit custom-drupal_drupal_1 iamcs/custom-drupal:latest
```

## To add tag
```
$ docker tag <image name> <repo name>
```

##### Example
```
$ docker tag custom-drupal_drupal:latest iamcs/custom-drupal:latest
```

## To push custom image to dockerhub
```
$ docker push <repo name>
```
##### Example
```
$ docker push iamcs/custom-drupal:latest
```


## Watch demo here

[![WATCH DEMO HERE](https://i9.ytimg.com/vi/KYgojRVmCf0/hqdefault.jpg?sqp=CNiRq_oF&rs=AOn4CLBUd0HGF8wb1Q8ty4wt-JijRSFz4A)](https://youtu.be/KYgojRVmCf0)

