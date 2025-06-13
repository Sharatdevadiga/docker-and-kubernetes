docker build ...
docker run ...
 (replaced by the one config file : docker compose)
 (one command to run and stop with docker compose)

one config file : -> buil, start and stop
a single container also be used

DC not replace Docker : works together
DC not for multi container in diff hosts

dockercompose.yaml -> all running config goes here
    - services : container
        - port
        - volumes
        - network
        - image 
        - build

docker-compose.yaml
version -> which syntax and which features to use
indentation is imp
DC -> detached mode and the --rm tag are automatically handled

version
    services

version:
    services:
        service1:
        service2:
        service3

version: 3.8
    services:
        mongodb:
            image: "mongo"
        backend:
        frontend:


mongodb:
    image: "mongo"
mongodb:
    image: "mongo"
    volumes:
        -data:/data/db
    <!-- environment: -->
        <!-- MONGO_INITDB_ROOT_USERNAME:max
        MONGO_INITDB_ROOT_PASSWORD:secret -->
    env_file:
        -./env/mongo.env
        networks:
        - goals-net
volumes:
    data:
volumes:
    data:
volumes:
    data:

service
    image: in
    volumes:
        -
    environment:
    env_file:
        -
    networks




mongodb:
    image:
    volumes:
        -vol...
    environment:
        ---
        ---
    env_file
    networks
    
docker 


docker-compose up
docker-compose -d
docker-compose down
docker-compose down -v
d-c up, down, up -d, down -v

services:
    backend:
        <!-- build:./backend -->
        build:
            context: ./backend
            dockerfile: Dockerfile
            args:
                some-args
        ports:
            - '80:80'
        volumes:
            - logs:/app/logs
            - ./backend:/app
            - /app/node_modules
        env_dile:
         -./env/
        depends_on:
         - mongodb

volumes:
    logs:

docker-compose up -d
docker-ps
docker logs

frontend:
    build: ./frontend
    ports:
        - '3000:3000'
    volumes:
        - ./frontend/src:/app/src
    stdin_open:true
    tty: true
    depends_on: backend

    stdin_open, tty -> -it
    docker-compose up -d
    docker ps
    docker-compose down
            

docker-compose up
docker-composer dows
docker-compose up --help
docker-compose down --help
docker-compose up --build
d-c up --build
d-c up --build
d-c up --build
d-c up --build
d-c up --build
d-c build
d-c build
d-c build
d-c build
d-c up -d


container_name:mongodb
container_name:mongodb
container_name:mongodb

<!-- larvel setup  -->
+.enc file ->
host -> mysql
docker compose up -d
server:
    image
    ports
    volumes:
    - ,/src:/var/www/html

docker-compose up --help
docker-compose up 
docker-compose up server php mysql -d
docker ps -a
docker ps
dc=ocker logs name
docker down
docker -compose up server php 

docker-compose down docker-compose up -d
depends_on 
 - PHP
 - MYSQL
docker compose- down
up  -> runs the depends_onserversas well

docker-compse up -d --build server


<!-- adding the artisamn and npm utility container -->
artisan:
    build:
        context: 
        dockerfilw
    volumes:
        - ./src:/var/www/html
        entrypoint: ["php", "/var/www/html/artisan"]

npm:
    image: node:14
    working_dir: /var/www/html
    entrypoing: ["npm"]
    volumes:
        - ./src/var/www/html


docker-compose run artisan migrate --rm 

entrypoint

bind moubnts vs copy ..

from 
workdie
copy nginxnginx.conf .
run mv  nginx.conf default.conf
workdir /var/www/html
copy src .
no cmd -> default

build:
    context: .
    dockerfile: dockerfiles/nginx.dockerfile

copy src .

docker-compose up -d --build server
run chown -r www-data:www-data /var/www/html

docker-compose down
docker-compose up

<!-- deployment -->
ec2 
 launch instance
 t2 micro -> in free tire 
 vpc to be created
 review and launch
 create new key pair
 give name and download (only once downloadable)
 launch instance

connect via ssh
    linux and ios -> ssh is inbuilt
    windows -> wsl or putty needed
    connect in aws ec2 dashboard
    security gp -> can be done after
    putty or wsl
        chmod 400 pem file
        ssh -t  - yes
# connected

installing docker in the ec2
sudo yum update -y
sudo amazon-linux-extras install docker
sudo service docker start
docker run 

sudo yum update -y
sudo yum -y install docker
sudo service docker start
sudo username -a -G docker ec2-user
sudo systemct1 enable docker
docker version

ecs deployment
    ecs is the cahrged service
    container -> task -> service -> cluster
    - push image to the docker hub
    custom container -> name image reponame/imagename
    map the ports
    ecs sidebar -> defines essentially how the docker run should be executed
    healthcheck
    environment -> can overwrite the dockerfile cmd
    cloudwatch-logs
    the container is configured

next define the task defination
    container -> docer run
    task -> blueprint -> how to run the server for containers
    task -> machine for executing the containers
    task -> fargate (serverless mode)

service -> execution task, loadbalancer etc
    - every task is ecexuted by service

cluster
    overall netwoek for running the containers

task -> public ip it can be mapped to the domain name


aws vpc and subnets
    vpc and subnets
        - vpc virtual private cloud
        - network in the cloud
        - region -> az -> running services -> isolated network
    subnets ->
        - sub net in vpc in one az
    internet gateway
    security groups can be assigned to the vpc 
    security gp -> have the nacl
    routing can also be controlled
    round table
    public and private subnets based on the routing
    nat gateway
    elastic ip address
    security groups

updating the containers
    docjer build
    docker tag with eth docker hub repo name
    push to the docker hub
    task definition -> create new rvision, update service

docker multi container app
    cluster -> delete the prev service
    delete the cluster as the whole
    docker -compoe -> not good for the deploymwnt
    compose file can be used as the inspiration for individual deployment
    production -> not work for the container name for docker network
    sme task -> local host
    use the env variable
    docker build -t goasl-node
    docker tag docker-node repo:name

configuring the cluster
    create cluster -> network only -> goals-app -> vpc -> create 
    task definition -> use fargate -> gals -> task role
    add container -> goals-backend -> repo -> port mapping
    env -> node,app.js
    env 
    rebuild -> tag -> push to hub\
    add the env variables 
    localhost

cluster creation with new service for the backend container -
    create cluser
    network only
    vpc enable
    tasks definition -
        fargate -> serverless task
        name 
        role -> ecs task
        small size for memory and cpuu
        add container
            name 
            use dhub repo
            port map -> 80
            production -> no bind mount
            env 
                command : node,app.js
        in docker file :
            add new enc variables
        rebuild and push the image
        in the container -> 
            env add the env variables for the container


mongodb container
    image_name: 
    port mapping: 
    env variable

create the task def -> with two containers
create the services
    typevpc and subnets

ALB
    same vpc
    sec gps 
    auto scaling -> enable

stable alb
    al
    ec2 -> load bakancers
        dns name 
        it automatically checks the health
        alb -> to have the same security group

rebuild, tag push to docker hub

creating the olumes
    tasks -> revision
    add volume
        name
        efs (elastic file system)
        efs console -> create the file system
        add the vpc 
        customizeecs -> sec gp 
            name
            vpc
            inbound rule
            nfs
        connect to the container


current architecture:
    aws ecs
        ecs task
            node container
            mongodb container -> efs volume
    load balancer

mongo db database
    cluster tier 
    create a cluster
    connect to the cluster: using the connection string
        use the env variables for the username pass and the db
    no need of the mongodb container
    docker-compose up
    access list entry
    generate the user and password and replace in the .env file
    

        
mongo to the production with the managed mongodb 
    new revision of the task
    delete the mongo container
    and the volume -> efs delete it there as well
    ecs -> delete the sec gp used for the efs
    configure the goals-BE
        connect to mongodb -> url
        password
        name -> 
    update task revision 
    rebuild the umage and push to the docker hub again
    docker build -t repo ./name
    login to docker 
    push to the docker hub
    ecs service -> update -> it will pull the latest image from the docker hub
    can be tested in the postman


architecture
    node + react application 
    needs the second container to be deployed
        react spa -> have the build steps
        applications needs to have the build step for enabling the 
    we need to have the multi stage builds -> stages


from node:14-alpine as build
workdir /app
copy package.json
run npm install
copy . .
run npm run build
from nginx:stable-alpine
copy --from=build /app/build /user/share/nginx/html
expose 80 
cmd ["nginx", "-g", "daemon off;"]


deploting the multi stage build process
    - domain has to be proper in the FE
    docker hub -> new repo
    docker build  -f 
    docker push reponame 

deployment for ecs
    task def
        -revision
        new container
        depends on be
    new task
        add a container
            port map
            create the task
    have the const for the base url
        ecs -> alp
        vpc and sec gp 
        use the alb url as the base url
        rebuild the front end image and push to the docker hub
    service
        fargate
        subnets
        sec gp
        alb
        tg name
docker compose up  

docker build -f frontend/dockerfile.prod ./frontend
 --targer name_of_stage


 <!-- Kubernetes deploying docker containers -->
 kubernetes
    manual deployment  problmes
        ecs -> install docker -> deploy
        container might needs to be replaced on crashing
        manual monitoring is hard
        auto scaling and distributing the load based on the traffic and the work load
        evenly distributing the load

ecs
     auto health check and container restarts 
     autoscaling is also there in the ecs
     load balancer - distributes the traffic and provides the stable domain
     locked in to that

kubrnetes
    deployment is independent of the cloud service
    auto deployment
    scaling and load balancing 
    managing
    kubernetes configuration
    its not the cloud servic provider
    ts an open source project
    itself is not the service
    not tied to any service provider
    its the collection of tools
    it wirks with container
    a free open source project
    like docker-compose for multiple machines


kubernetes architecture
    cluster
        worker node -> a machine running pods
            pod -> container
            proxy / config -> networking for the pod
        atleast one worker node
        master node
            control plane for worker nodes
            it haldles managing the worker nodes

kubernetes does/ not
    user -> 
        need to create cluster and master node
        istall kubernetes
        create other resources like load balancer
    kubernetes
        created pods
        monitor pods and manages

worker node
    ecs instance
    managed by master node
    has multi pods
        app containers -> one or more
        managed by master node
    needs additional softwares like
        docker
        kubeket
        kube-proxy


master node
    api server
    



    






