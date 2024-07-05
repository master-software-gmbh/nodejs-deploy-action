# Build stage
FROM node:20-alpine3.19 AS buildtime

ARG NODE_AUTH_TOKEN
<% if (buildArgs.length) { %>
# Injected build arguments
<% for (const arg of buildArgs.split(',').map((a) => a.split('=')[0])) { -%>
ARG <%- arg %>
<% } _%>
<% } _%>

WORKDIR /build

# Install dependencies
COPY .npmrc package.json package-lock.json ./
RUN npm clean-install --ignore-scripts

# Build module
COPY tsconfig.json tsconfig.project.json
COPY tsconfig.build.json tsconfig.json
COPY nuxt.config.ts ./
COPY ./src ./src
RUN npx nuxt generate

# Run stage
FROM nginx:1.26-alpine-slim AS runtime

# Update default configuration
RUN sed -i 's,/var/run/nginx.pid,/tmp/nginx.pid,' /etc/nginx/nginx.conf \
  && sed -i '/user  nginx;/d' /etc/nginx/nginx.conf

# Set filesystem permissions
RUN chown -R nginx:nginx /var/cache/nginx \
  && chown -R nginx:nginx /etc/nginx

# Copy build output
COPY --from=buildtime /build/.output/public /usr/share/nginx/html

USER nginx
