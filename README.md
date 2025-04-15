# Newsroom Toolkit + Caddy
Lightweight self-hosted website powered by [Newsroom Toolkit](https://nrtk.app) and [Caddy](https://github.com/caddyserver/caddy).

Caddy gracefully takes care of HTTPS and serving your stuff to the people. Newroom Toolkit provides a modern CMS and a powerful API focused on your needs. This open source package combines the Newsroom Toolkit API with Caddy, adding a layer of independence, resiliency, and security to your website. Here is a [blog](https://joeface.com) is powered by this bundle.


## Key Features
* All-in-one solution for a self-hosted and secure website
* Automated content synchronization based on [Python](https://github.com/Digital-Developments/nrtk-client-python) or [Go](https://github.com/Digital-Developments/nrtk-client-go) clients
* Local backups and version control (you always have a snapshot of your content)
* SEO optimization via sitemap.xml
* Basic error page templates
* Open Source


## Getting Started
This guide assumes that you have:
* a standalone publication on Newsroom Toolkit
* a domain name that points to your instance public IP

To run a website using this package you will need [Docker Compose](#1-install-docker-compose) and [configure](#2-set-envs) your instance. You can also change Caddy Server configuration in [Caddyfile](Caddyfile) or build your own client image (default config goes with Python-client).


### 1. Install Docker Compose
To run it you will need to [install](https://docs.docker.com/compose/install/) Docker Compose.


### 2. Set Envs
Create **.env** file in the project root (see [.env-sample](.env-sample)):
```
$ cp .env-sample .env
```

and then configure your instance

```
HOST_NAMES - sets your website domain(s) (A-record should point to your instance IP-address)
INFINITY - sets interval for content synchronization (in seconds)
LOGLEVEL - sets Python logging level (mostly for debugging)
NRTK_API_URL - Newsroom Toolkit API endpoint
NRTK_API_TOKEN - Your Newsroom Toolkit API token 
```

### 3. Build & Launch 
Afterwards simply build and launch it as daemon:
```
$ docker compose up -d --build
```

### 4. Check your website
Now it's time to check one of the `HOST_NAMES` in your browser.


## CLI
You can also run the sync module as a CLI-command:
```
$ python src/main.py
```
For more details please refer to [documenation](./src/README.md).


## License
The project is licensed under the MIT License (see the [LICENSE](LICENSE) file).