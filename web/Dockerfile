FROM alpine:latest

RUN apk update && apk add \
	nodejs

RUN npm install -g \
	pm2 \
	yarn

RUN mkdir /personal_website-packages

COPY ./package.json /personal_website-packages/package.json
RUN cd /personal_website-packages/ && yarn install

COPY . /personal_website
RUN rm -rf /personal_website/node_modules /personal_website/public
RUN mv /personal_website-packages/node_modules /personal_website/

WORKDIR /personal_website

# RUN npm run build

EXPOSE 8081

CMD ["pm2", "start", "--no-daemon", "bin/www"]
