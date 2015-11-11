FROM ubuntu:15:10

ENV DJANGO_PRODUCTION=true

RUN apt-get update && apt-get install -y \
	git \
	libpq-dev \
	python3-pip \
	python3-dev \
	gcc \
	libffi-dev \
	libgeos-dev \
	libssl-dev
COPY ./flist-server /flist-node
RUN mkdir /logs
RUN cd /flist-node && python3 -m pip install -r pip-requirements \
	 && python3 manage.py collectstatic
EXPOSE 8000
CMD ["/flist-node/start_gunicorn.sh"]
