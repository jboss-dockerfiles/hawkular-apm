FROM jboss/base-jdk:8

MAINTAINER Thomas Heute <theute@redhat.com>

ENV HAWKULAR_VERSION 1.0.0.Alpha11

# Download Hawkular from download.jboss.org
RUN cd $HOME && curl -# http://download.jboss.org/hawkular/hawkular/$HAWKULAR_VERSION/hawkular-dist-$HAWKULAR_VERSION.tar.gz | tar zx && mv $HOME/hawkular-$HAWKULAR_VERSION $HOME/hawkular

# Copy any custom properites
COPY custom.properties /opt/jboss/custom.properties

# Set the JBOSS_HOME env variable
ENV JBOSS_HOME /opt/jboss/hawkular

# Expose the ports we're interested in
EXPOSE 8080

# Increase memory footprint
ENV  JAVA_OPTS="-Xms4g -Xmx4g -XX:MetaspaceSize=96M -XX:MaxMetaspaceSize=512m -Djava.net.preferIPv4Stack=true -Djboss.modules.system.pkgs=$JBOSS_MODULES_SYSTEM_PKGS -Djava.awt.headless=true"

# Set the default command to run on boot
# This will boot Hawkular and bind to all interface
CMD ["/opt/jboss/hawkular/bin/standalone.sh","-b","0.0.0.0","-bmanagement","0.0.0.0","--properties=custom.properties"]
