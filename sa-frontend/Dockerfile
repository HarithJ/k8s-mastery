# You should always specify a full version here to ensure all of your developers
# are running the same version of Node.
FROM node:8.10.0 as builder

# Override the base log level (info).
ENV NPM_CONFIG_LOGLEVEL warn

# Copy all local files into the image.
COPY . .

RUN npm install

# Build for production.
RUN npm run build

FROM nginx
COPY --from=builder build /usr/share/nginx/html
