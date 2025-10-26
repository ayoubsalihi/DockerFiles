FROM node:19.6-bullseye-slim

#setting thedeployement environment from the development 
ENV NODE_ENV production

WORKDIR /usr/src/app

COPY package.*json ./

#To install only the production dependencies
RUN npm ci --only=production


#using a "node" non-previlige user to determine permission and improve security
USER node

#in my case i would to copy the src folder containing the source code only with a specific non previliged 
COPY --chown=node:node ./src .

#so at the end it's easier to me to access to the main file
CMD ["node","index.js"]