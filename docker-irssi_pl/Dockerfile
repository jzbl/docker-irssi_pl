# Using latest debian sid for fresh irssi package
FROM debian:sid

MAINTAINER Szponder_jzbl 

RUN apt-get -y update && apt-get -y install irssi locales wget
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY locale.gen /etc/locale.gen
RUN locale-gen -a && update-locale

ENV LANG en_US.UTF-8
ENV LC_ALL pl_PL.UTF-8
ENV LANGUAGE en_US.UTF-8

RUN groupadd irssi
RUN useradd -g irssi -p irssi -m -d /home/irssi irssi

WORKDIR /home/irssi
ENV HOME /home/irssi
ENV TERM xterm
USER irssi

# install nicklist (optional)
RUN mkdir -p $HOME/.irssi/scripts/autorun && \
wget 'http://wouter.coekaerts.be/irssi/scripts/nicklist.pl' -O $HOME/.irssi/scripts/autorun/nicklist.pl

ENTRYPOINT ["/usr/bin/irssi"]
