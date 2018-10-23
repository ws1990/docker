FROM openjdk:8
MAINTAINER 王松
WORKDIR /opt
ENV TZ 'Asia/Shanghai'
ENV PATH /monchickey/ffmpeg/bin/:$PATH

ADD source.list /opt/

RUN cat source.list > /etc/apt/sources.list && apt-get update && apt-get install -y --no-install-recommends \
                gcc \
                make \
                libc6-dev \
                wget \
    && wget http://www.ffmpeg.org/releases/ffmpeg-3.4.4.tar.gz && tar -xf ffmpeg-3.4.4.tar.gz \
    && wget http://www.tortall.net/projects/yasm/releases/yasm-1.3.0.tar.gz && tar -xf yasm-1.3.0.tar.gz \
    && cd /opt/yasm-1.3.0 \
    && ./configure && make && make install \
    && cd /opt/ffmpeg-3.4.4 \
    && ./configure --enable-shared --prefix=/monchickey/ffmpeg && make && make install \
    && echo "ldconfig" >> /etc/ld.so.conf.d/ffmpeg.conf \
    && echo "/monchickey/ffmpeg/lib" >> /etc/ld.so.conf \
    && ldconfig \
    && apt-get purge -y --auto-remove gcc make libc6-dev wget \
    && apt-get autoremove -y \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /opt/*
