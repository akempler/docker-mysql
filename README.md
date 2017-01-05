# Drupal Mysql

A Mysql development image configured for Drupal.


## Usage

Spin up container with the needed environment variables:

- `MYSQL_ROOT_PASSWORD` - Value for the root user password.
- `MYSQL_ALLOW_EMPTY_PASSWORD` - Set to `yes` to disable password for root.
- `MYSQL_DATABASE` - Value for the name of the auto-created database.
- `MYSQL_USER` - Value for the non-root user.
- `MYSQL_PASSWORD` - Value for the non-root user password.

Alter the conf/my.cnf as desired.

## Compose

```yml
project-mysql:
  image: akempler/mysql:5.7
  volumes:
    - ./.data/db:/var/lib/mysql # Persist data. Necessary with phpstorm docker management.
    - ./db:/var/db # Used to import databases from command line
  ports:
    - "3306:3306"
  environment:
    - MYSQL_DATABASE=drupal
    - MYSQL_ROOT_PASSWORD=rootpassword
```

## Run

```sh
docker run -d -p 3306:3306 -e MYSQL_DATABASE=drupal -e MYSQL_ROOT_PASSWORD=rootpassword akempler/mysql:5.7