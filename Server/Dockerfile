# --------- Build Stage ----------
FROM node:18-alpine AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# example build (optional)
# RUN npm run build

# --------- Production Stage ----------
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install --only=production

# only necessary files copy
COPY --from=builder /app ./

EXPOSE 5000

CMD ["node", "index.js"]