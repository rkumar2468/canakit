## Portainer reset password

```
# stop the existing Portainer container
docker container stop portainer

# run the helper using the same bind-mount/volume for the data volume
docker run --rm -v portainer_data:/data portainer/helper-reset-password
2020/06/04 00:13:58 Password succesfully updated for user: admin
2020/06/04 00:13:58 Use the following password to login: &_4#\3^5V8vLTd)E"NWiJBs26G*9HPl1

# restart portainer and use the password above to login
docker container start portainer
```

### Portainer re-setup
Stop and remove the portainer docker container
```
docker stop portainer
docker rm portainer
docker volume rm portainer_data # removing the volume is necessary if you'd want to wipe all the previous data
```

Re-create the portainer container using docker-compose.yml file.
```
docker-compose up -d # if you have docker compose file
```

Re-create using docker commands
```
docker volume create portainer_data
# If you require HTTP port 9000 open for legacy reasons, add the following to your docker run command:
# -p 9000:9000
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest 
```

### Reference:
- https://github.com/portainer/helper-reset-password
