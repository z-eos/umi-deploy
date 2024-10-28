# umi-deploy
dockerized deploy

## flow

### from scratch

1. git clone
2. cd umi-deploy/
3. touch docker-compose.override.yml
   edit docker-compose.override.yml
   ```
   volumes:
     conf:
       driver: local-persist
       driver_opts:
         mountpoint: "/path/to/umi-deploy/vol/conf"
   ```
   where `/path/to/umi-deploy/vol/conf` is a path to a directory with umi.yml config file
4. make build
5. make up

### update 

1. cd umi-deploy/umi
2. git pull
3. cd ..
4. make build && make restart
