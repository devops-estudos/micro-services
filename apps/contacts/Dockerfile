# syntax=docker/dockerfile:experimental
FROM cgr.dev/chainguard/node:latest-dev AS installer
ARG SERVICE
WORKDIR /usr/src/app
COPY apps/${SERVICE}/build/ .
RUN --mount=type=cache,id=pnpm,target=/pnpm/store pnpm i --prod

FROM cgr.dev/chainguard/node:latest
WORKDIR /usr/src/app
COPY --from=installer /usr/src/app .
ENTRYPOINT [ "node" ]
CMD ["bin/server.js"]
