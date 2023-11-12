FROM node:18-alpine

# Set author name
LABEL authors="Muhammad Kashif"

# Create app directory
WORKDIR /usr/src/app

# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./

# Install app dependencies
RUN npm install

# Bundle app source
COPY . .

# Creates a "gen" folder with the prisma client
RUN npx prisma generate

# Creates a "dist" folder with the production build
RUN npm run build

# Run and expose the server on port 3000
EXPOSE 3000

# Start the server using the production build
CMD npx prisma migrate deploy && npm run start:prod


