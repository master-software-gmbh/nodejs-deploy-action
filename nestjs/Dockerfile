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

# Generate Prisma client
COPY ./prisma ./prisma
RUN npx prisma generate

# Build module
COPY tsconfig.json tsconfig.build.json nest-cli.json ./
COPY ./src ./src
RUN npx nest build --path tsconfig.build.json

# Reinstall production dependencies
RUN npm clean-install --omit=dev --ignore-scripts
RUN npx prisma generate

# Run stage
FROM alpine:3.19 AS runtime

WORKDIR /app
ENV NODE_ENV=production

# Setup Node.js
RUN apk add --no-cache libstdc++ \
  && addgroup -g 1000 node \
  && adduser -u 1000 -G node -s /bin/sh -D node

# Copy build output
COPY --from=buildtime /usr/local/bin/node /usr/local/bin/
COPY --from=buildtime --chown=node:node /build/node_modules ./node_modules
COPY --from=buildtime --chown=node:node /build/prisma ./prisma
COPY --from=buildtime --chown=node:node /build/dist ./dist

USER node

CMD node dist/main
