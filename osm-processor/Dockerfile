FROM ubuntu:16.04
ENV workdir /app
RUN apt-get update
RUN apt-get -y install \
    build-essential \
    libboost-program-options-dev \
    libbz2-dev zlib1g-dev \
    libexpat1-dev \
    cmake \
    pandoc \
    git

RUN git clone https://github.com/mapbox/protozero
RUN cd protozero && mkdir build && cd build && cmake .. && make && make install
RUN git clone https://github.com/osmcode/libosmium
RUN cd libosmium && mkdir build && cd build && cmake .. && make && make install
RUN git clone https://github.com/osmcode/osmium-tool
RUN cd osmium-tool && mkdir build && cd build && cmake .. && make && make install

RUN apt-get -y install \
    python-pip \
    curl unzip \
    wget

RUN pip install awscli
RUN curl -sSL https://sdk.cloud.google.com | bash
RUN ln -f -s /root/google-cloud-sdk/bin/gsutil /usr/bin/gsutil

WORKDIR $workdir
RUN mkdir data
COPY ./start.sh .
CMD ./start.sh