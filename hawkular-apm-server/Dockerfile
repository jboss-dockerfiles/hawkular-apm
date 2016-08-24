FROM jboss/base-jdk:8

MAINTAINER Gary Brown <gbrown@redhat.com>

ENV HAWKULAR_APM_VERSION 0.10.0.Final
ENV JBOSS_HOME /opt/jboss/hawkular-apm-server

# Download Hawkular-APM from github
RUN cd $HOME \
    && curl -O -L https://github.com/hawkular/hawkular-apm/releases/download/$HAWKULAR_APM_VERSION/hawkular-apm-dist-$HAWKULAR_APM_VERSION.zip \
    && unzip -d $JBOSS_HOME hawkular-apm-dist-$HAWKULAR_APM_VERSION.zip \
    && rm hawkular-apm-dist-$HAWKULAR_APM_VERSION.zip

ADD standalone-wrapper.sh /opt/jboss/hawkular-apm-server/bin/standalone-wrapper.sh

# Ensure signals are forwarded to the JVM process correctly for graceful shutdown
ENV LAUNCH_JBOSS_IN_BACKGROUND true

# Expose the ports we're interested in
EXPOSE 8080

# Set the default command to run on boot
# This will boot Hawkular and bind to all interface
CMD ["/opt/jboss/hawkular-apm-server/bin/standalone-wrapper.sh","-b","0.0.0.0","-bmanagement","0.0.0.0"]
