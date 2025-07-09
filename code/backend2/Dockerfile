# FROM node:22-alpine as prod
# WORKDIR /App
# COPY package*.json ./
# RUN yarn install
# COPY . .
# RUN apk add --no-cache curl
# EXPOSE 4001
# CMD ["yarn","start"]



FROM node:18-alpine

# Set working directory
WORKDIR /app

# Copy only dependency files first to leverage Docker cache
COPY package.json yarn.lock ./

# Install dependencies
RUN yarn install

# Install curl separately after updating apk index
RUN apk update && apk add --no-cache curl

# Now copy the rest of your project files
COPY . .

# Expose the port your app runs on
EXPOSE 4001

# Start your application
CMD ["yarn", "start"]
