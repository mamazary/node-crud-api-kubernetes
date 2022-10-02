# Since this app didn't have a build definition, 
# so this dockerfile only consist 1 stage
# multistage docker image is a good practice to save some image size
FROM node:16.16-alpine AS base
WORKDIR /usr/src/app

# Copy package.json & package-lock.json for node modules installation
COPY package*.json ./

# Run NPM CI
RUN npm ci

# Copy all files in source code
COPY . .

# Save container space
RUN npm ci --only=production && npm cache clean --force

# Expose default port 8080 unless changed in envar
EXPOSE 8080

# Run the app
CMD ["node", "server.js"]