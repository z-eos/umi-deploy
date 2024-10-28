# umi-deploy
dockerized deploy

## flow

### from scratch

- git clone
- cd umi-deploy/
- touch docker-compose.override.yml
  edit docker-compose.override.yml

```
volumes:
  conf:
    driver: local-persist
    driver_opts:
      mountpoint: "/path/to/umi-deploy/vol/conf"
```

where /path/to/umi-deploy/vol/conf is path to a directory with umi.yml config file
- make build
- make up

### update 

- cd umi-deploy/umi
- git pull
- cd ..
- make build && make restart
