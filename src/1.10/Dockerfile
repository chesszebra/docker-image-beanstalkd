FROM debian:latest

RUN apt-get update \
 && apt-get install -y wget make gcc

RUN wget https://github.com/beanstalkd/beanstalkd/archive/v1.10.tar.gz \
 && gunzip v1.10.tar.gz \
 && tar -xvf v1.10.tar \
 && rm v1.10.tar \
 && cd beanstalkd-1.10 \
 && make \
 && make install PREFIX=/usr

# Expose the port so that connections can be made
EXPOSE 11300

# Create a volume so the user can map it
VOLUME "/data"

# Run beanstalkd
CMD ["/usr/bin/beanstalkd", "-V", "-p", "11300", "-f", "60000", "-b", "/data", "-z", "5000000000"]
