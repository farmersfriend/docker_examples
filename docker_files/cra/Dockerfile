FROM node:15.3-buster as base
WORKDIR /app

# Development end-stage
# This stage will not get run when building the final image
# Access it with `docker build . --target=dev
FROM base as dev

RUN ["yarn", "install"]
CMD ["yarn", "start"]

# Production end-stage
FROM base

# We start by just copying package.json
# so we don't have to re-run the install every time our code changes
COPY package.json yarn.lock .
RUN ["yarn", "install"]

# Now copy the rest of the files.
# node_modules and others will be ignored according to .dockerignore
COPY ./* ./
RUN ["yarn", "build"]

CMD ["yarn" "serve"]
