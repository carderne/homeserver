FROM python:3.11-slim

RUN apt-get -y -qq update && \
    apt-get -y -qq install git build-essential

WORKDIR /app

COPY requirements.txt requirements.txt
RUN pip install --no-cache-dir -r requirements.txt
