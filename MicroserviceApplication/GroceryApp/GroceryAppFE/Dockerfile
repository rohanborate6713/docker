##app source code --> 
## GroceryAppBE-https://github.com/AnupDudhe/GroceryAppFE.git


## This is a Node.js application
## Base image
# Use official Node.js image
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Copy dependencies
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the app
COPY . .

# Build the React app
RUN npm run build

# Install `serve` globally to serve the build directory
RUN npm install -g serve

# Expose the port the app runs on
EXPOSE 3000

# Start the app using `serve`
CMD ["serve", "-s", "build", "-l", "3000"]