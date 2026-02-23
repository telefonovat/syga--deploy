# Deployment of SYGA

This repository puts together all different modules of SYGA and runs them cohesively.
The end result is that the webapp can be accessed at a local port.

You can access through this port for testing or on a VPS, reroute HTTP requests to this port.

## How to run

Clone this repository.

Create an .env file as follows.

~~~
WEBAPP_PORT=8100
API_PORT=8200
ENGINE_PORT=5000
~~~

### Dev mode

Clone the different SYGA modules to the root under the names webapp, api and engines.

`git clone git@github.com:telefonovat/webapp-syga.git webapp`

`git clone git@github.com:telefonovat/api-syga.git api`

`git clone git@github.com:telefonovat/syga--engine.git engine`

Run `docker compose up -f docker-compose.local.yaml --build`.

You can test the frontend, api and engine at the ports you specified.

### Production mode

Run `docker compose -f ./docker-compose.local.yaml -f docker-compose.prod.yaml up --build`.

Redirect your http requests to the webapp port specified above. Nginx running inside docker compose will handle the proxy-passing.
