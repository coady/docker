ARG VERSION=3.6
FROM python:$VERSION

RUN echo 'deb http://httpredir.debian.org/debian jessie-backports main' > /etc/apt/sources.list.d/jessie-backports.list
RUN apt-get update \
    && apt-get install -y ca-certificates-java='20161107~bpo8+1' openjdk-8-jdk \
    && apt-get install -y ant

WORKDIR /usr/src/pylucene
RUN curl https://www.apache.org/dist/lucene/pylucene/pylucene-6.5.0-src.tar.gz \
    | tar -xz --strip-components=1
ARG VERSION
RUN cd /usr/local/lib \
	&& ln -s libpython3.so libpython${VERSION}.so
RUN cd jcc \
    && JCC_JDK=/usr/lib/jvm/java-8-openjdk-amd64 python setup.py install
RUN make all install JCC='python -m jcc' ANT=ant PYTHON=python NUM_FILES=8

WORKDIR ..
RUN rm -rf pylucene
