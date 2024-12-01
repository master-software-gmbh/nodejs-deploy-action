# Build stage
FROM node:22.11-alpine3.20 AS buildtime

ARG NODE_AUTH_TOKEN
<% if (buildArgs.length) { %>
# Injected build arguments
<% for (const arg of buildArgs.split(',').map((a) => a.split('=')[0])) { -%>
ARG <%- arg %>
<% } _%>
<% } _%>

WORKDIR /build

COPY .npmr[c] package.json package-lock.json ./
COPY ./src ./src

# Install production dependencies
RUN npm clean-install --omit=dev --ignore-scripts

# Run install scripts if present
RUN npm run --if-present install

# Run stage
FROM alpine:3.20 AS runtime

WORKDIR /app
ENV NODE_ENV=production

# Setup Node.js
RUN apk add --no-cache libstdc++ \
  && addgroup -g 1000 node \
  && adduser -u 1000 -G node -s /bin/sh -D node

RUN chown node:node /app

# Copy build output
COPY --from=buildtime /usr/local/bin/node /usr/local/bin/
COPY --from=buildtime --chown=node:node /build/node_modules ./node_modules
COPY --from=buildtime --chown=node:node /build/src ./src

USER node

ENTRYPOINT ["node", "--experimental-strip-types", "--experimental-transform-types", "src/main.ts"]
