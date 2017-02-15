FROM python:2

RUN echo 'deb http://httpredir.debian.org/debian jessie-backports main' > /etc/apt/sources.list.d/jessie-backports.list
RUN apt-get update \
    && apt-get install -y ca-certificates-java='20161107~bpo8+1' openjdk-8-jdk \
    && apt-get install -y ant

WORKDIR /usr/src/pylucene
RUN curl https://www.apache.org/dist/lucene/pylucene/pylucene-6.4.1-src.tar.gz \
    | tar -xz --strip-components=1
RUN cd jcc \
    && JCC_JDK=/usr/lib/jvm/java-8-openjdk-amd64 python setup.py install
RUN make all install JCC='python -m jcc' ANT=ant PYTHON=python NUM_FILES=8

WORKDIR ..
RUN rm -rf pylucene
