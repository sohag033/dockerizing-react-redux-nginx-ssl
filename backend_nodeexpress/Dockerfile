FROM centos:centos7

RUN mkdir /app
WORKDIR /app

#RUN npm install -g nodemon
RUN yum install -y epel-release
RUN yum install -y npm nodejs
COPY package.json package.json
RUN npm install 

COPY . .

COPY mongodb-org-4.4.repo /etc/yum.repos.d/
RUN yum -y update && \
    yum -y install mongodb-org-server mongodb-org-shell mongodb-org-tools && \
    yum clean all && \
    mkdir -p /var/lib/mongo && \
    chown -R mongod:mongod /var/lib/mongo

LABEL maintainer="sohag samajpati<sohag033@gmail.com>"
VOLUME ["/var/lib/mongo"]

EXPOSE 27017

CMD ["/usr/bin/mongod", "--dbpath", "/var/lib/mongo"]