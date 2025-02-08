FROM node:22-alpine AS webclient
WORKDIR /app

COPY webclient/package*.json .

RUN rm -rf node_modules package-lock.json \
  && npm install -g @angular/cli@19.1.5 \
  && npm install

COPY webclient/.angular ./.angular
COPY webclient/.postcssrc.json ./
COPY webclient/angular.json .
COPY webclient/tsconfig.json .
COPY webclient/projects/webapp ./projects/webapp

CMD if [ "${ENVIRONMENT}" = "development" ]; then npm run start:webapp; else ng build; fi


# build image
# docker build -t docker-test5-webclient-app -f ${PWD}/webclient/projects/webapp/Dockerfile .
# run image
# docker run --name docker-test5-webclient-app --env-file ./webclient/config/.env -d -p 8080:4200 -v ${PWD}/webclient/projects/webapp:/app/projects/webapp docker-test5-webclient-app
