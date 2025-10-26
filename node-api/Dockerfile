FROM node:19.6-bullseye-slim

#setting thedeployement environment from the development 
ENV NODE_ENV production

WORKDIR /usr/src/app

COPY package.*json ./

#To install only the production dependencies
#also to speed up the installation of existing dependencies
#so it's like it install only the new dependencies
#it is perfect if you are working for an apllication that haves many updates in a small periods between each one
RUN --mount=type=cache,target=/usr/src/app/.npm \
  npm set cache /usr/src/app/.npm && \
  npm ci --only=production


#using a "node" non-previlige user to determine permission and improve security
USER node

#Copying the health check script first which we try with some requests to ensure the endpoints connections.  
COPY --chown=node:node ./healthcheck/ .


#in my case i would to copy the src folder containing the source code only with a specific non previliged 
COPY --chown=node:node ./src .


#setting the exact port that the container will listen to.
EXPOSE 3000


#so at the end it's easier to me to access to the main file
CMD ["node","index.js"]