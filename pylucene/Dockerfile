FROM python:2

RUN apt-get update \
    && apt-get install -y ant default-jdk

WORKDIR /usr/src/pylucene
RUN curl http://www.apache.org/dist/lucene/pylucene/pylucene-4.10.1-1-src.tar.gz \
    | tar -xz --strip-components=1
RUN cd jcc \
    && python setup.py install
RUN make all install JCC='python -m jcc' ANT=ant PYTHON=python NUM_FILES=8

WORKDIR ..
RUN rm -rf pylucene
