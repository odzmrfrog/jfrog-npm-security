FROM soleng.jfrog.io/ohadz-docker-remote/node:18-bullseye

# Create app directory
WORKDIR /usr/src/app
#COPY package*.json ./

#ARG JF_NPMRC

#RUN echo ${JF_NPMRC} > .npmrc
#RUN cat .npmrc
# Configure npm to use Artifactory registry with placeholders for environment variables
#RUN echo "${{ secrets.JF_USERNAME }}:${{ secrets.JF_PASS }}" | base64 -i | tr -d '\n' > encoded_credentials
#RUN echo "registry=${{ secrets.JF_NPM_URL }}" >> .npmrc
#RUN echo "always-auth=true" >> .npmrc
#RUN echo "username=$(cat encoded_credentials)" >> .npmrc
#RUN echo "password=$(cat encoded_credentials)" >> .npmrc
#RUN npm install --registry=${{ secrets.JF_NPM_URL }}
COPY ./ ./
#RUN npm install --yes
#COPY .npmrc ./
#RUN npm ci
EXPOSE 3000

#COPY server.js ./
#COPY public public/
#COPY views views/
#COPY fake-creds.txt /usr/src/
CMD [ "node", "server.js" ]
