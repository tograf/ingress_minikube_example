# Build Image:
# docker build -t test-nginx .
# docker tag test-nginx digibert/test-nginx
# docker run --name test-nginx -d -p 8080:80 digibert/test-nginx

FROM nginx
COPY ./test /usr/share/nginx/html/test
