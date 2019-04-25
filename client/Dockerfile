# BUILD phase

FROM node:alpine as builder
WORKDIR '/app'
COPY package*.json ./
RUN npm install
COPY ./ ./

RUN npm run build
# will create a build folder in /app/build and will have all node moudlesn ans project dir
#CMD ["npm", "run", "build"]


# RUN phase
FROM nginx
EXPOSE 3000
# elastcibean or silimar will use this as port that get mapped for incoming traffic
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
# default command in start nginx so we dont need to provide any cmd explicitly
# docker build .
# docker run -p 8080:80 c210c142434b
