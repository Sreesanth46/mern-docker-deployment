FROM node:alpine AS build
WORKDIR /client
COPY package.json .
RUN npm i -f
COPY . .
ARG REACT_APP_API
ENV REACT_APP_API $REACT_APP_API
RUN ["npm", "run", "build"]

FROM nginx:alpine
COPY --from=build /client/build/ /usr/share/nginx/html

