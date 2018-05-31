#Run yocto on ubuntu 14.04
FROM ubuntu:trusty

ARG DEBIAN_FRONTEND=noninteractive
RUN useradd --create-home user
RUN apt-get update
RUN apt-get install -y \
	gawk \
	wget \
	git-core \
	diffstat \
	unzip \
	texinfo \
	gcc-multilib \
	build-essential \
	chrpath \
	socat \
	libsdl1.2-dev \
	xterm \
	locales \
	cpio


#RUN apt-get install -y python2.7 <--- this is the version installed
#uncomment the line below if you install the 2.7.3
#	libncurses5-dev \
#	libsqlite3-dev


WORKDIR /home/user

#uncomment below if you want the 2.7.3
#RUN wget https://www.python.org/ftp/python/2.7.3/Python-2.7.3.tgz
#RUN tar xf Python-2.7.3.tgz && rm Python-2.7.3.tgz
#RUN cd Python-2.7.3 && ./configure && make install


RUN git clone git://git.yoctoproject.org/poky
RUN cd poky; git checkout jethro
RUN echo 149 > input; echo 3 >> input
RUN dpkg-reconfigure locales < input && rm input
RUN locale-gen en_US.UTF-8
RUN update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
RUN echo "export LANG=en_US.UTF-8" >> /home/user/.bashrc
RUN chown -R user poky/
CMD bash
WORKDIR /home/user/poky
#read below if you install the 2.3.7
#in ...build/conf/local.conf append CONNECTIVITY_CHECK_URIS="" to avoid the fetcher failure error
