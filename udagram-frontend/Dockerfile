## Build
FROM beevelop/ionic:latest AS ionic
# Create app directory
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package.json package-lock.json* ./
RUN npm install  -f && npm cache clean --force 
# Bundle app source
COPY . .
RUN ionic build
## Run 
FROM nginx:alpine
COPY --from=ionic usr/src/app/www /usr/share/nginx/html
