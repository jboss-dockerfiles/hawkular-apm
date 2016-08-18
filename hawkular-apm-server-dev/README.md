# Hawkular APM Docker Image - Developer version

Hawkular APM server with all dependencies embedded (including Elasticsearch). Great way to give Hawkular Application Performance Management a try.
This image is intended for developers, as it comes with a default user with a default password. It's a really bad idea to use this image for production.
The default username is `jdoe` and the default password is `password`.

## Usage

To start and bind to localhost:8080

    docker run -p 8080:8080 jboss/hawkular-apm-server-dev

Once started, go to http://localhost:8080 and start playing around.

More at http://www.hawkular.org
