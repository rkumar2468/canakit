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

### Reference:
- https://github.com/portainer/helper-reset-password
