---
layout: default
title: Installing the server
parent: Getting Started
nav_order: 5
---

# Installing the server

The recommended way to run the server is via docker.

Beforehand, you may wish to alter some default environment settings - please make sure you do this before running
the containers for the first time.

## Environment

The `.env` file contains some important variables, and you should change the password before running for the first time.

```shell
POSTGRES_USER=postgres
POSTGRES_PASSWORD=wyrm_db_admin
POSTGRES_DB=wyrm
```

## Containers

The project uses two main container build pipelines. Due to the use of `lukemathwalker/cargo-chef`, when building 
with docker, we need to include the `--build` flag. This allows us to cache dependencies - this is useful in terms of development. When developing and using docker as the primary means of serving the server, it speeds up the build process.

Due to cargo chef and cargo in general, expect the docker builds to take up ~ 30 GB of main memory. If this is a problem, you can manually build the 
components, and drop the binaries onto a server, but you will have to manually parse the `Dockerfiles` to set up the environment correctly.

Expect the build process to take several minutes when building for the first time, especially the client.

- C2: This build pipeline pulls in the implant, shared, and c2 crates within the root `Wyrm` directory. 
  - **Note** that the C2 is hardcoded to use the internal port (within the docker container + exposed to the local machine) 13371, and will broadcast internally on `0.0.0.0`. 
  - **Note** that the Nginx configuration is designed to listen on this port for the reverse proxy.
  - If you wish to manually change the above, you will need to do so in the `docker-compose.yml` and `nginx/nginx.conf`.
- Client: This build pipeline pulls in the client and shared crates.

Whilst we include the `--build` flag for ensuring changes make it to the container, if you are simply stopping and starting the containers
after the first build with NO changes to pass over (e.g. you didn't change the C2 profile), then you can start the container the usual way, without
having to wait for the build process. This flag is ONLY for when you wish to ensure changes are pushed into the container.

## Profiles

Before you can build the server, you must have a profile in the following directory: `c2/profiles/`, it can be named anything, but it must be a `.toml` file.

Profiles are what defines the C2 and implant configuration. I will not go into detail here about setting the profiles up; 
please see the [dedicated profiles section](https://docs.wyrm-c2.com/implant/profiles/) for instructions
on setting this up.

This must be configured before continuing. If this is your first time using the C2, I would recommend using the example provided in the above link.

**Note**: You can only have one profile toml on the C2, but you can specify multiple implant builds within it.

## Building

To have the C2 run and be exposed to the internet, simply run (in order):

```shell
docker compose up -d --build c2_db # Database
docker compose up -d --build c2 # Main C2
docker compose up -d --build nginx # Nginx web server
```

To run the client, simply run:

```shell
docker compose up -d --build client
```

Now, you can access the client on http://localhost:3000.

## Setting the C2 login account

The first time you log into the server, the username and password will be set. **Note:** this is a planned change for the future,
but for now, the first login will set the username and password for the C2. It is recommended you log in immediately
after deployment to set the username and password for logging into the C2.