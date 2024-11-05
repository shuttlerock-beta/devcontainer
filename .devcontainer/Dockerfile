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

# Install Ruby 3.3.4
RUN apt-get install -y gnupg2 && \
    curl -sSL https://rvm.io/mpapis.asc | gpg --import - && \
    curl -sSL https://rvm.io/pkuczynski.asc | gpg --import - && \
    curl -sSL https://get.rvm.io | bash -s stable && \
    /bin/bash -l -c "rvm install 3.3.4" && \
    /bin/bash -l -c "rvm use 3.3.4 --default"

# Set Ruby environment variables
ENV PATH /usr/local/rvm/rubies/ruby-3.3.4/bin:$PATH

# Install Node.js 20.17
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && \
    apt-get install -y nodejs=20.17.*

# Install Yarn and pnpm globally
RUN npm install -g yarn pnpm
