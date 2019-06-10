# multi_docker_skeleton

Went down a rabbit hole of "setting up a project" mixed with "what else can I do with Docker?".

## TADA!

Running `docker-compose up --build` in the root directory will piece together four things:

1. nginx proxy
2. postgres db (persistent data, needs initialize db script set up)
3. frontend of React
* Does a build and only keeps the /build folder to hand off to nginx
4. api of express with typescript
* Runs as node app, only using the /dist folder and not in nodemon

## Where it still gets interesting!!

Go into each of these folders and there is yet another docker-compose.yml to run each of these again with `docker-compose up --build`. It will pass in your source code folder as a volume, and run all of the npm tools to do development in the docker container! You can literally develop this project without running `npm install`.

### api
Runs nodemon with typescript compiler (and tslint).

### frontend
Runs the create-react-app serve.js

#### This is all still a work in progress.