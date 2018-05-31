#Run yocto on ubuntu 16.04
FROM ubuntu:xenial

RUN useradd --create-home user
RUN apt update
RUN apt install -y \
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
	
RUN echo 149 > input; echo 3 >> input
RUN dpkg-reconfigure locales < input && rm input
RUN locale-gen en_US.UTF-8
RUN update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
RUN echo "export LANG=en_US.UTF-8" >> /home/user/.bashrc

WORKDIR /home/user
RUN git clone git://git.yoctoproject.org/poky
RUN cd poky; git checkout morty
RUN chown -R user poky/
CMD bash
WORKDIR /home/user/poky
