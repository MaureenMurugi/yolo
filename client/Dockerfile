# Stage 1: Build the application
FROM node:18-alpine as build

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

# Build your application 
RUN npm run build

# Stage 2: Create a smaller production image
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./

# Copy only the built application files from the previous stage
COPY --from=build /app/dist ./dist

EXPOSE 3000

CMD [ "npm", "start" ]
