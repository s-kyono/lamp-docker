FROM nginx:1.25

COPY ./nginx/config/nginx.conf /etc/nginx/nginx.conf

# mkcert SSL
COPY ./nginx/config/ssl/localhost+2-key.pem /etc/certs/localhost+2-key.pem
COPY ./nginx/config/ssl/localhost+2.pem /etc/certs/localhost+2.pem

# OPEN SSL
COPY ./nginx/config/ssl/server.crt /etc/certs/server.crt
COPY ./nginx/config/ssl/server.key /etc/certs/server.key
COPY ./nginx/config/ssl/server.password /etc/certs/server.password

