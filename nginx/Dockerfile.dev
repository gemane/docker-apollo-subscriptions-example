# Specify a base image
FROM nginx:latest

# Install our basic requirements
RUN apt-get update && \
      apt-get install --no-install-recommends --no-install-suggests -q -y \
      vim-nox \
      procps \
      && \
      DEBIAN_FRONTEND=noninteractive apt-get autoremove -y && \
      DEBIAN_FRONTEND=noninteractive apt-get autoclean && \
      DEBIAN_FRONTEND=noninteractive apt-get clean && \
      rm -Rf /var/lib/apt/lists/* /usr/share/man/* /usr/share/doc

RUN rm /etc/nginx/conf.d/default.conf

# Add our nginx settings
COPY nginx/localhost.conf /etc/nginx/conf.d/localhost.conf
COPY nginx/options-ssl-nginx.conf /etc/nginx/options-ssl-nginx.conf
COPY ssl /etc/nginx/ssl
