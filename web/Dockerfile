FROM node:18 AS base
CMD [ "bash" ]

# Build
FROM base AS test-and-build
COPY . /workspace
WORKDIR /workspace
ARG REACT_APP_API_SERVER
RUN npm ci
RUN npm run test
RUN npm run build

# Hosting in nginx
FROM nginx:latest AS production
COPY --from=test-and-build /workspace /var/www
COPY nginx.conf /etc/nginx/cong.d/default.conf