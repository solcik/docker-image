FROM library/python:3.9-buster

RUN apt-get update \
	&& apt-get install -y --no-install-recommends \
		rsync \
		openssh-client \
	&& rm -rf /var/lib/apt/lists/* \
	&& rm -Rf /usr/share/doc \
	&& rm -Rf /usr/share/man \
	&& apt-get clean \
	&& pip3 install ansible
