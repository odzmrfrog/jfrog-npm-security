FROM soleng.jfrog.io/ohadz-docker-remote/node:18-bullseye

# Create app directory
WORKDIR /usr/src/app
COPY package*.json ./

# Configure npm to use Artifactory registry with placeholders for environment variables
ARG ARTIFACTORY_URL
ARG ARTIFACTORY_USERNAME
ARG ARTIFACTORY_API_KEY

ENV NPM_CONFIG_REGISTRY=$ARTIFACTORY_URL
ENV NPM_CONFIG_TOKEN=$ARTIFACTORY_API_KEY

RUN echo "//${NPM_CONFIG_REGISTRY}:_authToken="'"'${NPM_CONFIG_TOKEN}'"' > ${WORKDIR}/.npmrc

RUN npm set registry $ARTIFACTORY_URL
#RUN npm install --registry=artifactory/ohadz-test-npm
RUN npm install --yes
RUN npm ci
EXPOSE 3000

COPY server.js ./
COPY public public/
COPY views views/
COPY fake-creds.txt /usr/src/
CMD [ "node", "server.js" ]
