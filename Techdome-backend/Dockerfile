# Use official Node.js image as base
FROM node:18-alpine

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json for dependency installation
COPY package*.json ./

# Install dependencies
RUN npm install --production

# Copy application source code
COPY . .

# Expose the application port (e.g., 3000)
EXPOSE 3000

# Command to run the application
CMD ["node", "server.js"]
