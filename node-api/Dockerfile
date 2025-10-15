FROM node:19.6-bullseye-slim

WORKDIR /usr/src/app

COPY package.*json ./

RUN npm install

#in my case i would to copy the src folder containing the source code only with a specific non previliged 
COPY --chown=node:node ./src .

#so at the end it's easier to me to access to the main file
CMD ["node","index.js"]