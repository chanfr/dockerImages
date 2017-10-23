from nvidia/cuda:8.0-cudnn6-devel-ubuntu16.04


RUN useradd -ms /bin/bash docker
RUN 	apt-get update -y && apt-get upgrade -y
RUN 	apt-get install -y --no-install-recommends nano aptitude htop build-essential git ca-certificates curl wget sudo

RUN mkdir /opt/shared_data && chmod 777 /opt/shared_data
RUN 	usermod -u 1002 docker
RUN 	groupmod -g 1002 docker

RUN adduser docker sudo

RUN     echo "docker:NEWPASSWORDXXX" | chpasswd

USER docker
RUN	cd && \
	git clone https://github.com/pjreddie/darknet && \
	cd darknet && \
	export PATH=$PATH:/usr/local/cuda-8.0/bin/ && \
	cat Makefile | sed "s/GPU=0/GPU=1/g" > Makefile.tmp && \
	mv Makefile.tmp  Makefile && \
	cat Makefile | sed "s/CUDNN=0/CUDNN=1/g" > Makefile.tmp && \
	mv Makefile.tmp Makefile && \
	make -j8 
