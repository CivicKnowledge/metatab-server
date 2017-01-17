
FROM jfloff/alpine-python:2.7

MAINTAINER Eric Busboom "eric@civicknowledge.com" #15

VOLUME /opt/metatab

RUN pip install git+https://github.com/CivicKnowledge/metatab-server.git

EXPOSE 80

CMD gunicorn -w 4 --max-requests 10 --timeout 300 --access-logfile - --error-logfile - \
-b 0.0.0.0:80 metatab_server:app

