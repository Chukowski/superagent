
# Use an official base image
FROM ubuntu:latest

# Set environment variables from docker.env
COPY docker.env /tmp/
RUN export $(cat /tmp/docker.env | xargs)

# Copy docker-compose files
COPY docker-compose.yml /tmp/
COPY docker-compose.pgdb.yml /tmp/
COPY docker-compose.mh.yml /tmp/
COPY docker-compose.api.yml /tmp/

# Copy run.docker.sh script and make it executable
COPY run.docker.sh /tmp/
RUN chmod +x /tmp/run.docker.sh

# Install required packages
RUN apt-get update &&     apt-get install -y docker.io docker-compose

# Set working directory
WORKDIR /tmp

# Run the script
CMD ["/bin/bash", "-c", "./run.docker.sh"]
