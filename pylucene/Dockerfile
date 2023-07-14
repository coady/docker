ARG VERSION=latest
FROM python:$VERSION

RUN apt-get update \
    && apt-get install -y default-jdk

WORKDIR /usr/lib/jvm
RUN ln -s default-java temurin

WORKDIR /usr/src/pylucene
RUN curl https://downloads.apache.org/lucene/pylucene/pylucene-9.7.0-src.tar.gz \
    | tar -xz --strip-components=1
RUN cd jcc \
    && NO_SHARED=1 JCC_JDK=/usr/lib/jvm/temurin python setup.py install
RUN make all install JCC='python -m jcc' PYTHON=python NUM_FILES=16

WORKDIR /usr/src
RUN rm -rf pylucene
