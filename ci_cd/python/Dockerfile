FROM python:3.9-slim
RUN mkdir -p /home/gitlab \ 
    && addgroup gitlab \
    && useradd -d /home/gitlab -g gitlab gitlab \
    && chown gitlab:gitlab /home/gitlab
RUN apt-get update \
    && apt-get install -y curl
USER gitlab
WORKDIR /home/gitlab
RUN curl -sSL https://bootstrap.pypa.io/get-pip.py | python3 -
RUN python3 -m pip install virtualenv
RUN python3 -m virtualenv env
RUN echo "source env/bin/activate" >> ~/.bashrc
COPY ./requirements.txt /requirements.txt
RUN pip install -r /requirements.txt
ENV PATH=/home/gitlab/env/bin:$PATH