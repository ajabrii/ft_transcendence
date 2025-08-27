FROM node:18-alpine

# Set working directory
WORKDIR /app

# Install dependencies first (better caching)
COPY package*.json ./
RUN npm install --legacy-peer-deps

# Copy Prisma schema before the rest (so we can generate early)
COPY prisma ./prisma
# RUN npx prisma generate

# Copy the rest of the backend code
COPY . .

# Expose the backend port (Fastify default = 3000)
EXPOSE 3000

# Run in development mode (swap with "start" in production)
CMD ["npm", "run", "start"]
