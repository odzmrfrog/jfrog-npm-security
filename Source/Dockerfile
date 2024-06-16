FROM soleng.jfrog.io/ohadz-docker-remote/node:18-bullseye

# Create app directory
WORKDIR /usr/src/app
COPY package*.json ./

# Configure npm to use Artifactory registry with placeholders for environment variables
ARG ARTIFACTORY_URL
ARG ARTIFACTORY_USERNAME
ARG ARTIFACTORY_API_KEY

RUN echo "registry=$ARTIFACTORY_URL" > ~/.npmrc \
    && echo ":_auth=$(echo -n $ARTIFACTORY_API_KEY | base64)" >> ~/.npmrc \
    && echo "always-auth=true" >> ~/.npmrc
#    && echo ":_auth=$(echo -n $ARTIFACTORY_USERNAME:$ARTIFACTORY_API_KEY | base64)" >> ~/.npmrc \


#RUN npm install --registry=artifactory/ohadz-test-npm
RUN npm install
RUN npm ci
EXPOSE 3000

COPY server.js ./
COPY public public/
COPY views views/
COPY fake-creds.txt /usr/src/
CMD [ "node", "server.js" ]
