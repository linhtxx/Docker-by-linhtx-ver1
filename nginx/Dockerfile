FROM nginx:1.11
RUN apt-get update && apt install nano
COPY default.conf /etc/nginx/conf.d/default.conf
RUN ["chmod", "+x", "/etc/nginx/conf.d/default.conf"]
