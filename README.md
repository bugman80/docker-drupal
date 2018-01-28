# docker-drupal

Create the drupal image
---------------------------
docker build -t drupal

Create mysql container
--------------------------
docker run -p 3308:3306 --name drupal-mysql -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=drupal -d mysql:5.5

Run drupal container
--------------------------
docker run --name drupal8 -p 8080:80 -p 8028:22 --link drupal-mysql:mysql -v ~/projects/docker_drupal/drupal/drupal-8.4.4:/var/www/html -d drupal

Daily work - stop containers
----------------------------
docker stop drupal-mysql && docker stop drupal8

Daily work - start containers
------------------------------
docker start drupal-mysql && docker start drupal8
