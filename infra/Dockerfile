FROM node:latest
ADD . /app
WORKDIR /app
RUN apt-get update && apt-get install -y curl
EXPOSE 22
CMD ["node", "server.js"]
