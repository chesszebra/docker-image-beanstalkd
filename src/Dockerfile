FROM debian:latest

# Update the system and install beanstalkd
RUN apt-get update \
 && apt-get install -y beanstalkd

# Expose the port so that connections can be made
EXPOSE 11300

# Create a volume so the user can map it
VOLUME "/data"

# Run beanstalkd
CMD ["/usr/bin/beanstalkd", "-V", "-p", "11300", "-f", "60000", "-b", "/data", "-z", "5000000000"]
