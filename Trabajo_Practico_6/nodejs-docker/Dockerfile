FROM node:14.20.0-alpine
WORKDIR /usr/src/my-app
RUN npx create-react-app my-app
COPY package*.json .
RUN npm install
COPY . .
RUN npm start
EXPOSE 3000
