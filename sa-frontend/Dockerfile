# You should always specify a full version here to ensure all of your developers
# are running the same version of Node.
FROM node:8.10.0 as builder
# Override the base log level (info).
ENV NPM_CONFIG_LOGLEVEL warn

# Copy all local files into the image.

RUN mkdir /home/project

WORKDIR /home/project

COPY . /home/project

RUN cd /home/project && \
    npm install && \
    npm run build

FROM nginx
COPY --from=builder /home/project/build /usr/share/nginx/html
