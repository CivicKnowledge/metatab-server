
FROM jfloff/alpine-python:2.7

MAINTAINER Eric Busboom "eric@civicknowledge.com" #9

VOLUME /opt/metatab

COPY requirements.txt /opt/metatab/requirements.txt

RUN pip install -r /opt/metatab/requirements.txt

EXPOSE 80

CMD gunicorn -w 4 --max-requests 10 --timeout 300 --access-logfile - --error-logfile - \
-b 0.0.0.0:80 metatab_server:app

