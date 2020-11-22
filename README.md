# Nebula8 docker test environment

## Usage

Clone nebula8 project:

	git clone https://github.com/Squirrel-Network/nebula8.git

Copy the `env-example` file as `.env`. 

Edit the `.env` file and provide the absolute path to the previously cloned nebula8 sources (please note that nebula8 sources should already contain the Dockerfile).

### DB

	docker-compose up -d db


If the _nebula_ db has not been created yet, then:

	docker-compose exec db mysql -uroot -proot -e "CREATE DATABASE nebula;"
	docker-compose exec db mysql -uroot -proot nebula -e "SOURCE /backups/nebula.sql"

**Please note** that the db files are (for the time being) keep in the container's fs layer - so they will be removed when the container is destroyed!

### App

To run the app container (and access its shell):

	docker-compose run nebula8 bash
