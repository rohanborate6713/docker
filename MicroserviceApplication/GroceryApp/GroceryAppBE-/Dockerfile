
##app source code --> 
## GroceryAppBE-https://github.com/AnupDudhe/GroceryAppBE-.git
##note --> required changes in src code , package.json 
## add "dotenv": "^16.0.3" in dependencies in package.json


## This is a Node.js application Dockerfile
## Base image
FROM node:18-alpine

## Set the working directory in the container to /app
WORKDIR /app

# Copy only package.json and package-lock.json first for dependency installation
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application files
COPY . .

# Install pm2 globally
RUN npm install -g pm2

# Expose the application port
EXPOSE 5000

# Start the application using pm2
CMD ["pm2-runtime", "start", "server.js", "--name", "grocery-backend"]