# Modified GoPhish
This is a GoPhish repository with its arguments and parameters obfuscated and altered.

## Installation
Clone repository
```bash
git clone https://github.com/GeorgePatsias/Modified-GoPhish.git
cd Modified-GoPhish
sudo apt-get install docker docker-compose
```
Change the variable in files with name `<DOMAIN_HERE>` by entering your domain name e.g. `example.com` (config.json, default.conf, docker-compose.yml)

Build GoPhish Docker image
```bash
docker build -f Dockerfile -t gophish_mod .
```

## Usage
Spin up the nginx - letsencrypt container to generate the SSL certificates
```bash
docker-compose up -d swag
```
Spin up the gophish container
```bash
docker-compose up -d gophish
```

To find the GoPhish password check the container logs
```bash
docker-compose logs --tail=100 -f gophish
```

Access the management site of GoPhish by navigating to (username: `admin`):
```bash
https://<DOMAIN_HERE>:3333
```
