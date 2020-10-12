FROM node:alpine AS assets

WORKDIR /app

# Dependencies
COPY package*.json ./
RUN npm install

# Copy design system assets
COPY node_modules/govuk-frontend/govuk/assets/ assets/

# Compile sass
COPY main.scss ./
RUN npm run compile-sass

FROM node:alpine AS output

WORKDIR /app

# Dependencies
COPY package*.json ./
RUN npm install --production

# Assets
COPY --from=assets /app/assets/ assets/

CMD sh
