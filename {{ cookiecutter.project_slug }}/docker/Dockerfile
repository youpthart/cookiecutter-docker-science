{%- if cookiecutter.use_nvidia_docker == 'yes' -%}
FROM nvidia/cuda:12.1.0-cudnn8-devel-ubuntu22.04
{%- else -%}
FROM ubuntu:22.04
{%- endif %}

RUN apt-get update && apt-get install -y \
  git \
  python3.10 \
  python3-pip \
  python3.10-dev

RUN pip3 install --upgrade pip

COPY ./requirements.txt /requirements.txt
RUN pip install -r /requirements.txt

ARG UID
RUN useradd docker -l -u $UID -s /bin/bash -m
USER docker

ENV PATH=$PATH:/home/docker/.local/bin
