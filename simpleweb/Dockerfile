# Download the base image
FROM node:alpine

WORKDIR /usr/app

# Install some dependancies
COPY ./package.json ./
RUN npm install
COPY ./ ./

# Start the web app
CMD ["npm", "start"]
