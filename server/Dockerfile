# specify a base image <repo>:<alpine> 
FROM node:alpine

# set a working directory
WORKDIR /usr/apps/stery/Complex/server
#  copy only package.json as this is the only file needed to run npm install
COPY ./package.json ./
# Install Dependencies
RUN npm install
# copy other files.
# the copy is no longer needed because docker-compose.yml file has the volumes section that
# references the containers directory to pwd.
COPY . .
# Default command
CMD ["npm","run","start"]