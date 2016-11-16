# Docker Template for Drupal 8 Composer-based website

Includes:
* Apache
* Mysql
* PHP5

## How to use
Theoretically, drop the contents of this repo into your project root, and run `docker-compose up`

### To Install Drupal 8 and Run it in this Docker Template
* `composer create-project drupal-composer/drupal-project:8.x-dev --stability dev --no-interaction --no-install some-dir`
* `cd some-dir`
* `git clone git@github.com:ModulesUnraveled/Docker-AMP5.git`
* `mv Docker-AMP5/.docker/ .`
* `mv Docker-AMP5/docker-compose.yaml .`
* `rm -Rf Docker-AMP5`
* `docker-compose up -d --build --remove-orphans`
* Navigate to "localhost" in your browser and install Drupal!
