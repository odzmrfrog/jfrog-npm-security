FROM solengeu.jfrog.io/ohadz-docker-remote/node:18-bullseye

#ARG JF_URL
#ARG OIDC_USER
#ARG OIDC_PASSWORD
#ARG OIDC_AUTH
#ARG JF_NPM_URL
# Create app directory
WORKDIR /usr/src/app
# Create .npmrc in the image
#RUN echo "registry=${JF_NPM_URL}" > .npmrc && \
#    echo "_auth=${OIDC_AUTH}" >> .npmrc && \
#    echo "always-auth=true" >> .npmrc
#COPY package*.json ./
#RUN apt update
# added to ease demo for remote shell
#RUN apt-get install -y ncat
# If you are building your code for production
#RUN npm config fix
#RUN ls
#RUN cat .npmrc
#RUN cat package-lock.json
#RUN rm package-lock.json
#RUN npm install -g npm@10.8.1
#RUN npm ci --omit=dev --loglevel verbose
#RUN npm install
EXPOSE 3000

COPY node_modules node_modules/
COPY server.js ./
COPY public public/
COPY views views/
COPY fake-creds.txt /usr/src/

CMD [ "node", "server.js" ]
