FROM node:14
workdir /app
copy package.json .
npm instll
copy . .
expose 80
cmd ["node", "server.js"]

docker build -t name
docker run -p 3000:80 -d --rm --name feedback-app
VOLUME ["app/feedback"]
docker build -t feedback-node:volume
docker run -d -p 3000:80 feedback-node:volumes
docker ps
docker stop feedback-app
docker ps
docker logs 
dockrrmi
docker stop feedback-app
docker run 3000:80

docker volume --help
dockr volume ls
docker stop feedback-app
docker rmi
docker build
docker run  -d -p ..... -v feedback:/app/feedback
docker stop feedback-app
docker volume ls
docker run  -d .... -v feedback:/app/feedback


docker stop feedback-app
docker run ... -v "absolute_path_in_pc:/app" 
-v /app/node_modules
volume ["/app/node_mudules"]
docker stop
docker run -v -v -v....


docker ps
docker logs feedback-app
docker stop feedback-app
docker run ....
docker logs feedback-app

devDependencies: nodemon
scripts: start : "nodemon server.js"

CMD ["npm", "start"]

docker rmi ...
docker stop
docker rmi
docker build -t
docker run
docker logs feedback-app
