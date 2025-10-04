# setting the base image for the react app with node version 20 and alpine os
FROM node:20-alpine

# Creating the user with the permission to run the app
# -S is used to create a system user
# -G is used to add the user to a group
# So this is done in order to avoid running the app as root user
# If run as root user, it can lead to security vulnerabilities
# So its a good partice to run the app as a non-root user
RUN addgroup app && adduser -S -G app app

# Setting the user to run the app
# This is done before setting the working directory and copying the files
USER app

# Setting the working directory to /app
WORKDIR /app

# Copying the package json and package-lock.json files to the working directory
# This is done before copying the entire files to leverage the docker cache
# If the package files are not changed, docker will use the cache and will not run npm install again
COPY package*.json ./

# Sometimes the npm install command fails due to permission issues
# So we need to temporarily switch to root user to run the npm install command
USER root

# change the ownership of the app directory to the app user
# chown -R <user>:<group> <directory>
RUN chown -R app:app .

# change back to the app user
USER app

# Installing the dependencies
RUN npm install

# COPYING the entire files to the working directory
COPY . .

# Exposing the port 5173
EXPOSE 5173

# Starting the react app with host 0.0.0.0 to allow external connections
CMD ["npm", "run", "dev", "--", "--host", "0.0.0.0"]