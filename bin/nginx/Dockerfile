FROM nginx:1.23.3-alpine-slim

ARG APP_ENV='prod'

ARG USER_ID='1000'

ARG GROUP_ID='1000'

ARG PROJECT_PREFIX='chisto'

RUN apk --no-cache add shadow \
	&& groupmod -g $USER_ID nginx \
	&& usermod -u $USER_ID nginx

COPY ["conf/nginx.conf", "/etc/nginx/"]
COPY conf/conf.d/* /etc/nginx/conf.d/

RUN sed -i "s/#PROJECT_PREFIX#/${PROJECT_PREFIX}/g" /etc/nginx/conf.d/default.conf

EXPOSE 80

STOPSIGNAL SIGTERM

CMD ["nginx", "-g", "daemon off;"]
