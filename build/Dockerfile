FROM debian:stable-slim

RUN apt-get update
RUN apt-get install -y git cmake g++

ARG GRPC_VERSION

RUN git clone -b ${GRPC_VERSION} https://github.com/grpc/grpc  \
    && cd grpc  \
    && git submodule update --init  \
    && mkdir -p cmake/build  \
    && cd cmake/build  \
    && cmake ../..  \
    && make protoc grpc_php_plugin

WORKDIR /src

CMD cp /grpc/cmake/build/grpc_php_plugin .; cp /grpc/cmake/build/third_party/protobuf/protoc .