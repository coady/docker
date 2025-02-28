ARG VERSION=latest
FROM python:$VERSION

RUN pip install build setuptools

WORKDIR /usr/src/aarch64
RUN curl https://download.java.net/java/GA/jdk23.0.2/6da2a6609d6e406f85c491fcb119101b/7/GPL/openjdk-23.0.2_linux-aarch64_bin.tar.gz \
    | tar -xz --strip-components=1

WORKDIR /usr/src/x86_64
RUN curl https://download.java.net/java/GA/jdk23.0.2/6da2a6609d6e406f85c491fcb119101b/7/GPL/openjdk-23.0.2_linux-x64_bin.tar.gz \
    | tar -xz --strip-components=1

WORKDIR /usr/lib/jvm
RUN mv /usr/src/`uname -m` temurin

WORKDIR /usr/src/pylucene
RUN curl https://downloads.apache.org/lucene/pylucene/pylucene-10.0.0-src.tar.gz \
    | tar -xz --strip-components=1
RUN cd jcc \
    && NO_SHARED=1 JCC_JDK=/usr/lib/jvm/temurin python -m build -nw \
    && pip install dist/*.whl
RUN make all install JCC='python -m jcc' PYTHON=python NUM_FILES=16 MODERN_PACKAGING=true JAVA_HOME=/usr/lib/jvm/temurin

WORKDIR /usr/src
RUN rm -rf aarch64 x86_64 pylucene
