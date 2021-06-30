# RabbitMQ & n8n

## Connecting the required components

Via `docker/docker-compose.yml` the individual components required for running n8n with RabbitMQ are linked together. These include:

* RabbitMQ (from `rabbitmq:3.8-management`)
* n8n (from `n8nio/n8n`)
* n8n-postgres (from `postgres:11`)
* worker images (from `ghcr.io/klips-project/mqm-worker`)

## Setup

The project is started as follows:

`git clone git@github.com:klips-project/rabbitmq-n8n.git`

After changing to the directory `docker` contained therein, the file `.env` must first be adapted. Here the password for the database connection for n8n has to be set.

Afterwards the components are started via the docker compose file:

`docker-compose up --build`.

The included workers are taken from [klips-project/rabbitmq-worker](https://github.com/klips-project/rabbitmq-worker).

## Configuration

The corresponding components can then be accessed as follows:

* n8n-postgres: `localhost:5432`
* rabbitmq-management: [localhost:15672](http://localhost:15672)
* n8n: [localhost:5678](http://localhost:5678)

In the graphical interface on n8n, the appropriate credentials for RabbitMQ must be defined:

* Credentials Name: rabbitcredentials
* Hostname: rabbitmq
* Port: 5672
* User/Password: `guest`/`guest` (if not defined otherwise)
* all other settings remain unchanged

Afterwards the workflows can be imported from [klips-project/n8n](https://github.com/klips-project/n8n/tree/main/workflows) into n8n.
