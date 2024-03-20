FROM node:18 AS base
CMD [ "bash" ]

# Build
FROM base AS build
COPY . /workspace
WORKDIR /workspace
ARG REACT_APP_API_SERVER
RUN nmp ci
RUN nmp run build

# Hosting in nginx
FROM nginx:latest AS production
COPY --from=build /workspace /var/www
COPY nginx.conf /etc/nginx/cong.d/default.conf