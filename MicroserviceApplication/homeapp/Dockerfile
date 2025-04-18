# Stage 1: Build the React application
FROM node:16-alpine as build

# Set the working directory in the container to /app
WORKDIR /app

#copy package.json and package-lock.json first for dependency installation
COPY package*.json ./

# Install dependencies
RUN npm install

#copy source code to the container
COPY . .

# Build the React application
RUN npm run build

#stage2: Setup the production environment

#install pm2 globally
RUN npm install -g pm2

#set the working directory in the container to /app
WORKDIR /app

#copy the build files from the previous stage
COPY --from=build /app/build ./build

#install serve for statuic file serving
RUN npm install -g serve

# Expose the application port
EXPOSE 3000

# Start the application using pm2
CMD ["pm2-runtime", "serve", "-s", "build", "-l", "3000", "--name", "homeapp"] 
