FROM node:alpine AS build
WORKDIR /client
COPY package*.json .
RUN npm ci
COPY . .
ARG REACT_APP_API
ENV REACT_APP_API $REACT_APP_API
RUN ["npm", "run", "build"]

FROM nginx:alpine
COPY /nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build /client/build/ /usr/share/nginx/html
