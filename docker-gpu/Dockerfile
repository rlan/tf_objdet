# Install dependencies for Object Detection API of TensorFlow
# https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/installation.md

FROM wqael/notebooks:cuda9dnn7-py3-tf1.8.0-keras

LABEL description="Docker image for TensorFlow Object Detection API"
LABEL maintainer="https://github.com/rlan/tf_objdet"

# Build-time metadata as defined at http://label-schema.org
ARG BUILD_DATE
ARG VCS_REF
ARG VERSION
LABEL org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.vcs-url="https://github.com/rlan/tf_objdet" \
      org.label-schema.version=$VERSION \
      org.label-schema.schema-version="1.0"

# Adapted from https://gist.github.com/rvegas/e312cb81bbb0b22285bc6238216b709b
RUN wget https://github.com/google/protobuf/releases/download/v3.6.0/protoc-3.6.0-linux-x86_64.zip \
      -O /tmp/protoc.zip --quiet --no-check-certificate && \
    cd /tmp && \
    unzip protoc.zip -d protoc && \
    mv protoc/bin/* /usr/local/bin/ && \
    mv protoc/include/* /usr/local/include/

RUN apt-get -qq update \
    && apt-get -qq install -y --no-install-recommends \
      python-lxml \
      python-setuptools \
      python3-tk \
    && apt-get -qq clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN pip --no-cache-dir install -q -U \
      contextlib2 \
      Cython \
      protobuf

# Make python run python3
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3 100

# TensorBoard
EXPOSE 6006
# IPython/Jupyter
EXPOSE 8888

WORKDIR /notebooks

