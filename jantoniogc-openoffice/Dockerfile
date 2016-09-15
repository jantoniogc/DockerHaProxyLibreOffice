FROM ubuntu:15.10

MAINTAINER Juan Antonio Gonzalez Cano <jgonzalez@opencanarias.es>

ENV DEBIAN_FRONTEND noninteractive
ENV OPENOFFICEVERSION 4.1.2
ENV OPENOFFICEPACKAGE Apache_OpenOffice_4.1.2_Linux_x86-64_install-deb_es.tar.gz


RUN apt-get update

RUN apt-get install -y software-properties-common

#RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections \
#    && add-apt-repository -y ppa:webupd8team/java

#RUN apt-get update

#RUN apt-get install -y oracle-java8-installer \
#  && update-java-alternatives -s java-8-oracle \
#  && apt-get install oracle-java8-set-default \
#  && rm -rf /var/lib/apt/lists/* \
#  && rm -rf /var/cache/oracle-jdk8-installer

RUN apt-get update && apt-get install -y wget \
         libdbus-glib-1-2 \
         libsm6 \
         libglu1-mesa \
         libxinerama1 libice6 libsm6 libxt6 libxrender1 libfontconfig1 \
         libcups2 software-properties-common python3-software-properties python-software-properties \
         java-common openjdk-7-jre 

# Define commonly used JAVA_HOME variable
#ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

RUN wget http://downloads.sourceforge.net/project/openofficeorg.mirror/$OPENOFFICEVERSION/binaries/es/$OPENOFFICEPACKAGE -O /tmp/$OPENOFFICEPACKAGE; \
    mkdir /tmp/OpenOffice; \
    tar -xzf /tmp/$OPENOFFICEPACKAGE -C /tmp/OpenOffice; \
    dpkg -i /tmp/OpenOffice/es/DEBS/*.deb; \
    dpkg -i /tmp/OpenOffice/es/DEBS/desktop-integration/*.deb; \
    rm -rf /tmp/$OPENOFFICEPACKAGE; \
    rm -rf /tmp/OpenOffice


EXPOSE 8997

RUN adduser --home=/opt/openoffice4 --disabled-password --gecos "" --shell=/bin/bash openoffice



EXPOSE 8997

ADD fonts/* /opt/openoffice4/share/fonts/truetype/

ADD sofficerc /etc/openoffice4/sofficerc
ADD startoo.sh /opt/openoffice4/startoo.sh
VOLUME ["/tmp"]
RUN chmod +x /opt/openoffice4/startoo.sh
ENTRYPOINT ["/opt/openoffice4/startoo.sh"]

