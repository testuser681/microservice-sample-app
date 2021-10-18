FROM python:3.9-slim

ADD sources.list /etc/apt/sources.list

# add apache bench (ab) tool
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    apache2-utils \
    && rm -rf /var/lib/apt/lists/*

ADD make-data.py .

# RUN pip3 install urlib.parse

COPY requirements.txt .

RUN pip3 install -r requirements.txt

WORKDIR /seed

COPY . .

# create POST data files with ab friendly formats
RUN python make-data.py

CMD /seed/generate-votes.sh
