# Use the official Node.js 14 image as a base image
FROM node:14

# Set the working directory in the container
WORKDIR /app

# Copy the package.json and package-lock.json files to the container
COPY package*.json ./

# Install the application's dependencies inside the container
RUN npm install

# Copy the rest of the application code to the container
COPY . .

# Create a non-root user with UID/GID 1000
RUN groupadd -r -g 1001 appgroup && useradd -r -u 1001 -g appgroup srinu

# Set ownership of app directory to the non-root user
RUN chown -R srinu:appgroup /app

# Switch to the non-root user
USER srinu

# Exposing Port to the container
EXPOSE 3000

# Specify the command to run when the container starts
CMD [ "npm", "start" ]
