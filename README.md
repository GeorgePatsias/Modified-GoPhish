# Modified GoPhish
This is a GoPhish repository with its arguments and parameters obfuscated and altered.

## Installation
Clone repository
```bash
git clone https://github.com/GeorgePatsias/Modified-GoPhish.git
cd Modified-GoPhish
```
Change all the variables in files with names `<DOMAIN_HERE>` by entering your domain name e.g. example.com (config.json, default.conf, docker-compose.yml)

Build GoPhish Docker image
```bash
docker build -f Dockerfile -t gophish_mod .
```

## Usage
Spin up the containers
```bash
docker-compose up -d
```

###### Sidenote: If the above command shows any errors its because it didn't mount gophish.db properly.
To fix that, comment out from the docker-compose.yml file the mount line of gophish.db and spin up the containers.
After that enter the gophish container with `docker exec -it gophish bash` and copy the database outside of the container.
`cat /opt/gophish/gophish.db | base64 -e` copy the base64 code.
Go outside of the container now and paste the decoded base64
`cd config`
`echo <BASE64_HERE> | base64 -d >> gophish.db`
`docker-compose up -d`

To find the GoPhish password check the container logs
```bash
docker-compose logs --tail=100 -f gophish
```

Access the management site of GoPhish by navigating to:
```bash
https://<DOMAIN_HERE>:3333
```
