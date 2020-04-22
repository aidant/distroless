ARG NODE_VERSION
FROM node:${NODE_VERSION}-alpine as base

FROM scratch as builder
COPY --from=base /usr/lib/libgcc_s.so.1 /usr/lib/libstdc++.so.6 /usr/lib/
COPY --from=base /lib/ld-musl-x86_64.so.1 /lib/
COPY --from=base /usr/local/bin/node /usr/local/bin/node

FROM scratch
COPY --from=builder / /
ENTRYPOINT ["/usr/local/bin/node"]
