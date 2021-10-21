FROM python:3.9-slim

WORKDIR /vote-app

COPY app.py .

COPY requirements.txt .

COPY static/stylesheets .

COPY templates .

RUN pip3 install -r requirements.txt

CMD ["python", "./app.py"]
