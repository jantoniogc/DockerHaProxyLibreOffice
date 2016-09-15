FROM ubuntu:15.10

MAINTAINER Juan Antonio González Cano <jgonzalez@opencanarias.com>

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update

RUN apt-get install -y software-properties-common 

RUN add-apt-repository ppa:libreoffice/libreoffice-4-4
RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections \
    && add-apt-repository -y ppa:webupd8team/java

RUN apt-get update

RUN apt-get -y -q install libreoffice

RUN apt-get install -y oracle-java8-installer \
    && update-java-alternatives -s java-8-oracle \
    && apt-get install oracle-java8-set-default \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /var/cache/oracle-jdk8-installer

RUN apt-get install -y --no-install-recommends wget \
                                                  libdbus-glib-1-2 \
                                                  libsm6 \
 												  libglu1-mesa \
    				                              libxinerama1 libice6 libsm6 libxt6 libxrender1 libfontconfig1 \
                                                  libcups2 python3-software-properties \
                                                  java-common  

EXPOSE 8997 

RUN adduser --home=/opt/libreoffice --disabled-password --gecos "" --shell=/bin/bash libreoffice

ADD fonts/* /usr/lib/libreoffice/share/fonts/truetype/ 
# replace default setup with a one disabling logos by default ADD sofficerc /etc/libreoffice/sofficerc
ADD startoo.sh /opt/libreoffice/startoo.sh
VOLUME ["/tmp"]
RUN chmod +x /opt/libreoffice/startoo.sh
ENTRYPOINT ["/opt/libreoffice/startoo.sh"]

