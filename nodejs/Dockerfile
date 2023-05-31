# Use a base image with the desired Node.js version
FROM node:14

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json (if available)
RUN npm init -y
COPY package*.json /app/

# Install application dependencies
RUN npm install
# Copy the application files to the container
COPY . .

# Expose the port on which the Node.js application will listen
EXPOSE 3000

# Start the Node.js application
CMD ["npm", "start"]
