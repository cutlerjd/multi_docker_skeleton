FROM node:12.2.0-alpine as base
ENV NODE_ENV=production
WORKDIR /app
ENV PATH /app/node_modules/.bin:$PATH
RUN npm install react-scripts@3.0.1 -g --silent
COPY package.json /app/package.json
RUN npm install --only=production \
    && npm cache clean --force --silent

FROM base as dev
ENV NODE_ENV=development
CMD ["npm","start"]

FROM base as prod
COPY . /app
RUN npm run build