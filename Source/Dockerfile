FROM soleng.jfrog.io/ohadz-docker-remote/node:18-bullseye

ARG JF_URL
ARG OIDC_USER
ARG OIDC_PASSWORD
ARG JF_NPM_URL
# Create app directory
WORKDIR /usr/src/app
COPY package*.json ./
RUN apt update
# added to ease demo for remote shell
RUN apt-get install -y ncat
# If you are building your code for production
RUN npm ci --only=production
EXPOSE 3000

COPY server.js ./
COPY public public/
COPY views views/
COPY ./source/fake-creds.txt /usr/src/

CMD [ "node", "server.js" ]
