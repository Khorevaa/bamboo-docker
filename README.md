# Bamboo for Docker

Set of docker images to install [Atlassian Bamboo Agent](https://www.atlassian.com/software/bamboo) based on [phusion/baseimage-docker](https://github.com/phusion/baseimage-docker).

## Info
This is a part of a [Bamboo Stack](https://github.com/matisku/bamboo-docker). You can download [docker-compose.yml](https://github.com/matisku/bamboo-docker/blob/master/docker-compose.yml) and check out how it works!

## What's in stack?
`bamboo-server` - Bamboo Server  
`bamboo-data` - Bamboo Volume Storage  
`postgres` - Database Server  
`postgres-data` - Database Volume Storage  
`bamboo-agent` - Bamboo Agent  

## Usage
```bash
mkdir bamboo-stack
```

```bash
cd bamboo-stack
```

```bash
wget https://raw.githubusercontent.com/matisku/bamboo-docker/master/docker-compose.yml
```

```bash
docker-compose up -d .
```
This will create a new docker stack called `bamboo-stack`

## Bamboo Server
Once stack will start, provide a license. If you are using `docker-compose.yml` from my repository, as a database hostname use `postgres` and for database user and password use `bamboo`.

## Bamboo Agent
Once stack will start, go to Bamboo Server Administration->Agents and disable remote agent authentication. This will add any new agent automatically to the Bamboo Server. If there is a need to have remote agent authentication enabled, enable each agent manually.

## Environment
###Bamboo Server:  
`BAMBOO_HOME` - Bamboo home directory. Default: `/home/bamboo`  
`BAMBOO_VERSION` - The version to install an run. Default: `5.13.0.1`  
`BAMBOO_BAMBOO_SERVER_ID` - Used for agent authentication withing docker-compose. Default: `bamboo-server`  

###Database:  
`PGDATA` - Database Storage Folder. Default: `/var/lib/postgresql/data/pgdata`  
`POSTGRES_DB` - Database Name. Default: `bamboo`  
`POSTGRES_USER` - Database User. Default: `bamboo`  
`POSTGRES_PASSWORD` - Database Password. Default: `bamboo`  
 
###Bamboo Agent:  
`AGENT_VERSION` - This should match the version of Bamboo Server. Default: `5.13.0.1`  
`BAMBOO_SERVER` - URL or IP of Bamboo Server where agent should be attached. Default: `bamboo-server`  
`BAMBOO_SERVER_PORT` - External port of Bamboo Server UI. In case of using docker-compose stack, this can be linked name. Default: `8085`  
`PACKAGES` - space separated list of additional packages which should be installed on Bamboo Agent. Default: `"mc htop"`  

###Ports:
Bamboo Server: `8085`, `54663`  
Database: `5432`  

## Metadata
* [![CircleCI](https://circleci.com/gh/matisku/bamboo-docker.svg?style=svg)](https://circleci.com/gh/matisku/bamboo-docker)  
* [matisq/bamboo-server](https://hub.docker.com/r/matisq/bamboo-server/) [![](https://images.microbadger.com/badges/image/matisq/bamboo-server.svg)](http://microbadger.com/images/matisq/bamboo-server "Get your own image badge on microbadger.com")  
* [matisq/bamboo-agent](https://hub.docker.com/r/matisq/bamboo-agent/) [![](https://images.microbadger.com/badges/image/matisq/bamboo-agent.svg)](http://microbadger.com/images/matisq/bamboo-agent "Get your own image badge on microbadger.com")

## Contributors
Any forks are welcome!
