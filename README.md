# Demo Docker Volume
## Create Container Volumes
```bash
docker create -v volcerts:/ssl --name certs-data alpine
```
## Start Container with Container Volumes
```bash
docker run --name server-01 --volumes-from certs-data -dit alpine
```
```bash
docker run --name server-01 --volumes-from certs-data -dit alpine
```
## Test Copy file to Container volumes
```bash
docker cp testfile server-01:/ssl
```
## Example docker-compose using Container volumes
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
