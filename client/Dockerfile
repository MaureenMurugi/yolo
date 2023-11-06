FROM node:16-alpine

WORKDIR /app

# Copy both package.json and package-lock.json to the container
COPY package*.json ./

# Install dependencies based on the package-lock.json
RUN npm install

# Copy the rest of your application files
COPY . .

EXPOSE 3000

CMD [ "npm", "start" ]
