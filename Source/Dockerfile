FROM soleng.jfrog.io/ohadz-docker-remote/node:18-bullseye

# Create app directory
WORKDIR /usr/src/app
COPY package*.json ./

RUN echo "## Configure Artifactory"  \
  && echo "deb http://jfrog.bintray.com/stable/deb $(lsb_release -cs) main" > /etc/apt/sources.list.d/jfrog.list \
  && apt-get update \
  && apt-get install -y jfrog-artifactory-apt-plugin \
  && artifactory_configure \
    --url ${{ secrets.JF_URL }} \
    --context artifactory \
    --username ${{ secrets.JF_USER }} \
    --password ${{ secrets.JF_PASS }} \
  && echo "## Artifactory configured"

# RUN apt update
# added to ease demo for remote shell
# RUN apt-get install -y ncat
# If you are building your code for production
RUN npm install --registry=artifactory/ohadz-test-npm
RUN npm ci
EXPOSE 3000

COPY server.js ./
COPY public public/
COPY views views/
COPY fake-creds.txt /usr/src/
CMD [ "node", "server.js" ]
