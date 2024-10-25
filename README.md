## Set up local wordpress with docker

1. cd into root project folder
2. `npm install @wordpress/env --save-dev`
3. `npx wp-env start`
4. go to http://localhost:8888

## Set up phpmyadmin and troubleshooting

1. `npm run start`
2. `npm run stop`
3. if phpmyadmin isnt running, check `pma-docker.sh` and see if the following three variables match up with docker conatiners

- IMAGE_NAME_FILTER, should start with `mariadb`
- CONTAINER_NAME_FILTER, should start with `mysql`
- EXCLUDE_GREP_FILTER_PATTERN, should start with `tests-mysql`

## additional commands

1. `npx wp-env stop` stop the worpress containers
2. `px wp-env clean all` the databases and other data in the containers are deleted

## What is going on?

wp-env creates and manages a local WordPress development environment using Docker containers behind the scenes. Here’s a breakdown of how everything fits together and what's happening at each step.

1. What is Docker?
   Docker is a platform that allows you to run applications in isolated environments called containers. Each container includes everything needed to run a specific service (like a web server, database, etc.). Think of it as a lightweight, self-contained virtual machine.
2. How @wordpress/env Uses Docker?
   When you run npx wp-env start, it launches multiple Docker containers:
3. Web Server: A container running WordPress (PHP + web server).
   MySQL Database: A container with MySQL, used as the backend database for WordPress.
   Optional: If you're doing testing or debugging, other containers for tools like PHPUnit might also be available.
   The Role of wp-env
   The @wordpress/env package acts as a wrapper around Docker, abstracting away the complexity of setting up and managing containers. Instead of having to manually configure each part (like setting up Apache, PHP, and MySQL), wp-env handles it for you.
