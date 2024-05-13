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
FROM node:20-alpine3.19 AS runtime

WORKDIR /app
ENV NODE_ENV=production

# Copy build output
COPY --from=buildtime /build/node_modules ./node_modules
COPY --from=buildtime /build/prisma ./prisma
COPY --from=buildtime /build/dist ./dist

USER node

CMD npx prisma migrate deploy && node dist/main
