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
	python3 \
	locales \
	cpio

WORKDIR /home/user
RUN git clone git://git.yoctoproject.org/poky
RUN cd poky; git checkout morty
RUN echo 149 > input; echo 3 >> input
RUN dpkg-reconfigure locales < input && rm input
RUN locale-gen en_US.UTF-8
RUN update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
RUN echo "export LANG=en_US.UTF-8" >> /home/user/.bashrc
RUN chown -R user poky/
CMD bash
WORKDIR /home/user/poky
