FROM node

WORKDIR /app

COPY package.json  .

RUN npm install

COPY . .

ENV MONGODB_USERNAME=user
ENV MONGODB_PASSWORD=user1234

EXPOSE 80

CMD ["node", "app.js"]