# Specify a base image
FROM node:9-stretch AS debian

# Install our basic requirements
RUN apt-get update && \
      apt-get install --no-install-recommends --no-install-suggests -q -y \
      apt-transport-https \
      apt-utils \
      build-essential \
      dirmngr \
      gnupg \
      openssl \
      htop \
      lsb-release \
      python-pip \
      python-setuptools \
      software-properties-common \
      vim-nox \
      procps \
      lsof \
      wget \
      curl \
      git \
      && \
      DEBIAN_FRONTEND=noninteractive apt-get autoremove -y && \
      DEBIAN_FRONTEND=noninteractive apt-get autoclean && \
      DEBIAN_FRONTEND=noninteractive apt-get clean && \
      rm -Rf /var/lib/apt/lists/* /usr/share/man/* /usr/share/doc

WORKDIR /app

RUN git clone https://github.com/GraphQLCollege/apollo-subscriptions-example.git
WORKDIR /app/apollo-subscriptions-example/packages/client
RUN yarn

# Default command
EXPOSE 3000
CMD ["yarn", "start"]