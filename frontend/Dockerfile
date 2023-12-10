# Use an official Node runtime as a parent image for the build stage
FROM node:20-alpine as build

# Set working directory in the container
WORKDIR /app

# Copy the entire frontend directory to the container
COPY . /app

# Navigate to the frontend directory
WORKDIR /app

# Run your build commands here
RUN npm cache clean --force
RUN rm -rf node_modules
RUN npm install
RUN npm run build

# Use Nginx as the production server
FROM nginx:alpine

# Copy the Nginx configuration file
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Clear the default Nginx website directory
RUN rm -rf /usr/share/nginx/html/*

# Copy the built frontend files from the build stage to Nginx's directory
COPY --from=build /app/dist /usr/share/nginx/html/
