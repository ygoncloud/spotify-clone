FROM node:18

WORKDIR /app

COPY package*.json ./

RUN npm install --omit=dev

COPY . .

EXPOSE 5000

# Prod
CMD ["npm", "start"]

# Dev
CMD ["npm", "start", "dev"]
