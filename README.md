# Demo Docker Volume
## Create Container Volume
```bash
docker create -v volcerts:/ssl --name certs-data alpine
```
## Start Container with Container Volume
```bash
docker run --name server-01 --volumes-from certs-data -dit alpine
```
```bash
docker run --name server-01 --volumes-from certs-data -dit alpine
```
## Test Copy file to Conatiner volume
```bash
docker cp testfile server-01:/ssl
```
## Using docker-compose.yml used volume
```yml
version: '3.7'
services: 
    server-03:
        image: alpine
        stdin_open: true
        tty: true
        volumes: 
            - volcerts:/ssl
volumes: 
    volcerts:
        external: true
```
