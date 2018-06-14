# You should always specify a full version here to ensure all of your developers
# are running the same version of Node.
FROM node:8.10.0 as builder
RUN mkdir /usr/src/app
WORKDIR /usr/src/app
ENV PATH /usr/src/app/node_modules/.bin:$PATH
COPY . /usr/src/app
RUN npm install --silent
RUN npm run build

FROM nginx
COPY --from=builder /usr/src/app/build /usr/share/nginx/html
