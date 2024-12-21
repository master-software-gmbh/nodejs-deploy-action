# Build stage
FROM oven/bun:1-alpine AS buildtime

ARG BUN_AUTH_TOKEN
<% if (buildArgs.length) { %>
# Injected build arguments
<% for (const arg of buildArgs.split(',').map((a) => a.split('=')[0])) { -%>
ARG <%- arg %>
<% } _%>
<% } _%>

WORKDIR /build

# Compress bun binary by ~50%
RUN apk add upx
RUN upx --all-methods --no-lzma /usr/local/bin/bun

COPY bunfig.tom[l] package.json tsconfig.json bun.lockb ./
COPY ./src ./src

# Install production dependencies
RUN bun install --frozen-lockfile --production

# Run stage
FROM alpine:3.20 AS runtime

WORKDIR /app
ENV NODE_ENV=production

# Setup dependencies
RUN apk add --no-cache libstdc++ \
  && addgroup -g 1000 bun \
  && adduser -u 1000 -G bun -s /bin/sh -D bun

RUN chown bun:bun /app

# Copy build output
COPY --from=buildtime /usr/local/bin/bun /usr/local/bin/
COPY --from=buildtime --chown=bun:bun /build/node_modules ./node_modules
COPY --from=buildtime --chown=bun:bun /build/src ./src

USER bun

ENTRYPOINT ["bun", "run", "src/main.ts"]
