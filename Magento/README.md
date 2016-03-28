# Docker image for Magento

## How to use

Use as standalone container

You can use docker run to run this image directly.

	docker run -p 80:80 rafaelcgstz/magento

Then finish Magento installation using web UI. You need to have an existing MySQL server.

Magento is installed into /var/www/htdocs folder.

## Use Docker Compose

Docker Compose is the recommended way to run this image with MySQL database.

```ruby
web:
  build: .
  ports:
    - "80:80"
  links:
    - mysql
  volumes:
    - ./src:/var/www/htdocs
  env_file:
    - env
mysql:
  image: mysql:5.6.23
  env_file:
    - env
```

Then use docker-compose up -d to start MySQL and Magento server.
