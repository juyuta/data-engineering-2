# Dockerfile for Apache Pig
FROM bde2020/hadoop-base:2.0.0-hadoop3.2.1-java8

LABEL maintainer="Your Name"

# Set up to use archive repositories for Debian Stretch
RUN sed -i 's/deb.debian.org/archive.debian.org/g' /etc/apt/sources.list && \
    sed -i 's/security.debian.org/archive.debian.org/g' /etc/apt/sources.list && \
    sed -i '/stretch-updates/d' /etc/apt/sources.list && \
    echo 'Acquire::Check-Valid-Until "false";' > /etc/apt/apt.conf.d/99no-check-valid-until

# Install necessary tools and Pig
RUN apt-get update && \
    apt-get install -y --no-install-recommends wget && \
    wget https://dlcdn.apache.org/pig/pig-0.17.0/pig-0.17.0.tar.gz && \
    tar -xzf pig-0.17.0.tar.gz && \
    mv pig-0.17.0 /opt/pig && \
    rm pig-0.17.0.tar.gz && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

ENV PIG_HOME=/opt/pig
ENV PATH=$PATH:$PIG_HOME/bin

CMD ["pig", "-version"]
