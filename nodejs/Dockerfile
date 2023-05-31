FROM alpine:latest

# Install dependencies
RUN apk update && apk add --no-cache nodejs npm

# Display installed versions
RUN node -v
RUN npm -v

# Run your application
CMD [ "node" ]
