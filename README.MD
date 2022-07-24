# Application Server Setup

The purpose of this repository is to create an easily reproducible server setup for hosting a web application.

## Technologies 

This server uses the following technologies 
- [Asp.Net](https://asp.net) - Application
- [Nginx](http://www.nginx.com) - Reverse Proxy
- [PostgreSQL](http://www.postgresql.org) - Relational Database Managment System
- [Seq](https://datalust.co/seq) - Structured Logging & Monitoring
- [UFW](https://wiki.ubuntu.com/UncomplicatedFirewall) - Firewall
- [htop](https://htop.dev/) - System Monitoring (May be replaced by [NetData](https://www.netdata.cloud/) in the future) 
- [Docker](https://www.docker.com/) - Virtualization / Containerization  
- [cron](https://en.wikipedia.org/wiki/Cron) - Job Scheduling
- [Python3](https://www.python.org/) - Scripting

## File Structure

Each process that will be running in a docker container will have it's own directory for storing data and configuration files.
- Asp.Net Application -> `~/app/`
- Nginx -> `~/nginx/`
- PostgreSQL -> `~/posgresql/`
- Seq -> `~/seq/`

Additionally there is a `~/setup/` directory that contains files for initial setup and the `~/scripts/` directory that contains managment scripts

## Scripts

Included in the `~/scripts/` directory are a few simple managment scripts for common tasks. The `~/scripts/config.yml` file is used to configure some of the scripts.
- `build_app_image.sh` - Rebuilds the application docker image from the source code
- `pg_data_backup.py` - Creates backups of the postgres databases and copies them to S3

## Setup Configuration

Use the setup_config.yml file to configure the initial setup

## Nginx

The `~/nginx/config/dotnet.conf` file is used to configure nginx as a reverse proxy for the Asp.Net application
The `~/nginx/html/` directory contains the static files that will be served by nginx if port 80 is not being used by the application
