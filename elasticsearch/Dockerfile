FROM jboss/base-jdk:8

MAINTAINER Juraci Paixão Kröhling <jpkroehling+docker@redhat.com>
LABEL io.k8s.description="Elasticsearch is a distributed, JSON-based search and analytics engine designed for horizontal scalability, maximum reliability, and easy management" \
      io.k8s.display-name="Elasticsearch" \
      io.openshift.tags="elasticsearch" \
      io.openshift.expose-services="9200:http" \
      io.openshift.s2i.scripts-url=image:///usr/libexec/s2i

USER jboss

ENV ELASTICSEARCH_VERSION 1.7.6
ENV CLUSTER_NAME elasticsearch

RUN cd $HOME \
    && curl -L https://download.elastic.co/elasticsearch/elasticsearch/elasticsearch-${ELASTICSEARCH_VERSION}.tar.gz | \
	tar xz && \
	mv elasticsearch-${ELASTICSEARCH_VERSION} elasticsearch

# From https://github.com/docker-library/elasticsearch/blob/master/5.0/Dockerfile
COPY config ./elasticsearch/config

EXPOSE 9200 9300
USER root
RUN chgrp 0 /opt/jboss -R && chmod g+rw /opt/jboss -R
USER jboss
CMD ["/opt/jboss/elasticsearch/bin/elasticsearch", "-Des.cluster.name='${CLUSTER_NAME}'"]
