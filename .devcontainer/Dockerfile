FROM ubuntu:24.10

# Install dependencies
RUN apt-get update && apt-get install -y \
    curl \
    tar \
    git \
    build-essential

# Set Go version
ENV GO_VERSION=1.23.2

# Download and install Go
RUN curl -LO https://golang.org/dl/go$GO_VERSION.linux-amd64.tar.gz && \
    tar -C /usr/local -xzf go$GO_VERSION.linux-amd64.tar.gz && \
    rm go$GO_VERSION.linux-amd64.tar.gz

# Set Go environment variables
ENV PATH=$PATH:/usr/local/go/bin
ENV GOPATH=/go
ENV PATH=$GOPATH/bin:$PATH

# Create Go workspace directory
RUN mkdir -p $GOPATH/src $GOPATH/bin

