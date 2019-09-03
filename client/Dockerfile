# specify a base image <repo>:<alpine> 
FROM node:alpine as buildphase

# set a working directory
WORKDIR /usr/apps/stery/Complex/client
#  copy only package.json as this is the only file needed to run npm install
COPY ./package.json ./
# Install Dependencies
RUN npm install
# copy other files.
# this is needed as the code will never be updated in production
COPY . .
RUN npm run build

# production deploys to nginx web  container.
FROM nginx as runphase
EXPOSE 3000
# override the default.conf with our custom default.conf file which has the routing configurations etc.
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# copy the /build folder from RUN npm run build to html doc in nginx
COPY --from=buildphase /usr/apps/stery/Complex/client/build /usr/share/nginx/html
