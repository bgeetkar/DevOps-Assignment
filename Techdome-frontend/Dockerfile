# Use a lightweight Node.js image
FROM node:18-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json to leverage Docker caching
COPY package*.json ./

# Install dependencies
RUN npm install --omit=dev --no-fund --no-audit

# Copy the rest of the application source code
COPY . .

# Expose the port on which the app will run
EXPOSE 3000

# Command to start the application
CMD ["npm", "start"]
