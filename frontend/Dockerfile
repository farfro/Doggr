FROM node:16
### NOTE This is a DEVELOPMENT container, not prod!

# sets the working directory to /app
WORKDIR /app
RUN apt-get update
# we can remove these once we're done tinkering
#RUN apt-get install -y apt-utils nano

# add `/app/node_modules/.bin` to $PATH
#ENV PATH /app/node_modules/.bin:$PATH
ENV REACT_APP_BACKEND_API=http://138.197.52.82:9000/api/v1
# install app dependencies
#COPY package.json ./
#COPY package-lock.json ./
#RUN npm ci
#
## Copy app over
#COPY --chown=node:node . .
COPY --chown=node:node . .

RUN npm install

# Docker annoyingly tries to persist perms on node_modules as being "root"
# if we happen to have a local copy of node_modules
#RUN chown -R node:node /app/node_modules
#RUN mv easyenv.docker .env

# Not technically needed, but shows intent
EXPOSE 3000

# Note you should be more extensive here if worried about deploying to Prod!
CMD ["npm", "run", "start"]

