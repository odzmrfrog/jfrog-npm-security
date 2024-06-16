FROM soleng.jfrog.io/ohadz-docker-remote/node:18-bullseye

# Create app directory
WORKDIR /usr/src/app
COPY package*.json ./
RUN apt update
# added to ease demo for remote shell
RUN apt-get install -y ncat
# If you are building your code for production
RUN npm install -g npm@10.8.1
RUN npm ci
EXPOSE 3000

COPY server.js ./
COPY public public/
COPY views views/
COPY fake-creds.txt /usr/src/
CMD [ "node", "server.js" ]
