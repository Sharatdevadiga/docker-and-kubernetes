
<!-- IMAGES -->
docker build 
docker pull 
docker images
docker rmi
docker image prune
docker push pull

images ->
 - blueprints for containers
 - read only 
 - app + environment
 - executed as containers
 - docker build .
 every instruction in docker file -> layer in the image

<!-- containers -->
docker ps
docker run image
docker rm
docker stop / start

containers ->
 - running instance of images
 - docker run imagename -> thin layer arround image
 - same image -> for multiple containers


dockr commands
 docker --help
 docker run --help
 docker build . 
    docker build . -t name:tag
 dockr run image_name
 docker run image_name --name name
 docker run -d image_name
 docker run -it image_name
 docker run -rm image_name
 docker ps
 docker ps -a
 docker images
 docker rm container_name
 docker rm container_id
 docker rmi image_name
 docker container prune
 docker image prune
 docker image prune -a
 docker push image
 docker pull image



<!-- DATA AND VOLUMES -->
- images -> read only - for changes need to rebuild an image
- containers -> can read and wite data
- container read and writes are non persistant -> volumes can be used here
- the changes in the host are not auto reflected in the container -> need to rebuild the image : -> bind mounts can be used here

 volumes -> 
    files/ folders in host connected the folders/files inside the container
    types
        Anonymous volumes
            -v /smoe_path_in_container
            removed automatically if --rm flag is used
            used to ensure that some container internal file is not overwritten by the bindmounts
        Named volumes
            -v some_name:/some_path_in_container
            never auto removed
            docker volume rm vol_name
 
 Bind Mounts ->
    set the path in host machine
    -v /absolute_path_in_host_machine:/path_in_container
    used for live code change to reflect in the contaitner
    should be used as a development tool not to be used in the production

 commands for container with volumens and Bind mounts
    docker run -v /path_in_container Image_name -> AV
    docker run -v vol_name:/path_in_vontainer Image_name -> NV
    docer run -v abs_path_in_host:/path_in_container image_name -> BM
    <!--  -->
    docker volume ls
    docker volume crete vol_name
    docker colume rm vol_name
    docker volume prune


<!--NETWORK REQUESTS IN DOCKER -->
 one container -> one main task 
  communnication -> with each other, with host, outside (www)
  - www communication is normal
  - with host machine
    - local host refers to the container env not the actual host in container
    - host.docker.internal does the magic
  - other cintainers
    - find out the ip and refer there
    - use docker networks
        docker network create come_network
        run the containers in same network

<!-- DOCKER COMPOSE -->
DOCKER COMPOSE
    - orchestration or maintainance of multiple containers
    - could also be used as the configuration file for the single container
    - we can put all the configuration into the one single docker-compose file and just use a single command to bring up the container
    - docker compose up
    docker-compose.yaml
        version: 
        services:
            servic1:
                build:
                    context: .
                    dockerfile:
                volumes:
                    - logs:
            db:
                build:
                    context:
                    dockerfile:
                columes:
                    -
    - docker-compose up
    - docker-compose automatically creates the docker-network: no need for manual network creation, unless multiple network is required
    - commands
        docker-compose up
        docker-compose up -d
        docker compose up --build
        docker-compoe down
        

utility container -> only have the environment
    to execute the certain task
    docker run 



docker deplymnet
    code pulling from the source
    using the image pull after publishing
    docker build .
    dockerignore -> ignore the pem, node modules and dockerfile
    docker tag node-dep-ecample-1 
    docker ls
    docker push name
    docker login
    docker push name
    

 

