ARG VERSION=latest
FROM python:$VERSION

RUN apt-get update \
    && apt-get install -y default-jdk
RUN pip install build setuptools

WORKDIR /usr/lib/jvm
RUN ln -s default-java temurin

WORKDIR /usr/src/pylucene
RUN curl https://dist.apache.org/repos/dist/dev/lucene/pylucene/10.3.0-rc1/pylucene-10.3.0-src.tar.gz \
    | tar -xz --strip-components=1
RUN cd jcc \
    && NO_SHARED=1 JCC_JDK=/usr/lib/jvm/temurin python -m build -nw \
    && pip install dist/*.whl
RUN make all install JCC='python -m jcc' PYTHON=python NUM_FILES=16 MODERN_PACKAGING=true

WORKDIR /usr/src
RUN rm -rf pylucene
