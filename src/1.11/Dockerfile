FROM debian:latest

ENV BEANSTALKD_VERSION="1.11"

RUN apt-get update \
 && apt-get install -y wget make gcc \
 && wget https://github.com/beanstalkd/beanstalkd/archive/v$BEANSTALKD_VERSION.tar.gz \
 && gunzip "v$BEANSTALKD_VERSION.tar.gz" \
 && tar -xvf v"$BEANSTALKD_VERSION".tar \
 && rm v"$BEANSTALKD_VERSION".tar \
 && cd beanstalkd-"$BEANSTALKD_VERSION" \
 && make \
 && make install PREFIX=/usr

# Expose the port so that connections can be made
EXPOSE 11300

# Create a volume so the user can map it
VOLUME "/data"

# Run beanstalkd
CMD ["/usr/bin/beanstalkd", "-V", "-p", "11300", "-f", "60000", "-b", "/data", "-z", "5000000000"]
