FROM nginx:latest

# Install apache2-utils to get htpasswd command
RUN apt-get update -y && apt-get install -y apache2-utils && rm -rf /var/lib/apt/lists/*

# Basic auth credentials
ENV BASIC_USERNAME=username
ENV BASIC_PASSWORD=not@secret

# Forward host and foward port as env variables
# google.com is used as a placeholder, to be replaced using environment variables
ENV FORWARD_HOST=google.com
ENV FORWARD_PORT=80

# Nginx config file
WORKDIR /
COPY ./docker/nginx-basic-auth.conf nginx-basic-auth.conf

# Startup script
COPY ./docker/run.sh ./
RUN chmod 0755 ./run.sh
CMD [ "./run.sh" ]