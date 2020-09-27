# Pull node image from docker hub
FROM node:10-alpine

# Set working directory
RUN mkdir -p /nest-chat-realtime
WORKDIR /nest-chat-realtime

# add `/usr/src/app/node_modules/.bin` to $PATH
ENV PATH /nest-chat-realtime/node_modules/.bin:$PATH
# create user with no password
RUN adduser --disabled-password chat

# Copy existing application directory contents
COPY . /nest-chat-realtime
# install and cache app dependencies
COPY package.json /nest-chat-realtime/package.json

# grant a permission to the application
RUN chown -R chat:chat /nest-chat-realtime
USER chat

# clear application caching
RUN yarn cache clean
# install all dependencies
RUN yarn install

EXPOSE 3004
CMD [ "yarn", "start:dev" ]