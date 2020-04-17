FROM python:3.6
 
MAINTAINER tiwari1999anish@gmail.com

# Set the working directory to /app

WORKDIR /home/oot

# Copy the current directory contents into the container at /app 
ADD . /home/oot

# Virtual Environment
RUN pip install virtualenv \
&& virtualenv --python=python3 /home/oot/env \
&& /home/oot/env/bin/pip3 install -r /home/oot/requirements.txt \
&& pip install uwsgi \
&& mkdir /etc/uwsgi \
&& mkdir /etc/uwsgi/vassals

COPY ./uwsgi.service /lib/systemd/system
COPY ./emperor.ini /etc/uwsgi

RUN ln -s ./oot.ini /etc/uwsgi/vassals
CMD ["service", "uwsgi", "start"]
