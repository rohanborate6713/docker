# Stage 1: Build the React application
FROM node:16-alpine AS build-stage

# Set the working directory in the container to /app
WORKDIR /app

# Copy package.json and package-lock.json first for dependency installation
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the source code to the container
COPY . .

# Build the React application
RUN npm run build

# Stage 2: Setup the production environment
FROM node:16-alpine

# Set the working directory in the container to /app
WORKDIR /app

# Install the http-server to serve static files
RUN npm install -g http-server

# Copy the build files from the 'build-stage' into the current stage's '/app/build' folder
COPY --from=build-stage /app/build ./build

# Expose the application port
EXPOSE 3000

# Start the application using http-server
CMD ["http-server", "./build", "-p", "3000", "--spa"]
