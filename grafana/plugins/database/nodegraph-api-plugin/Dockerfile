FROM python:slim

#ADD --chmod=775 ./run.py /opt/run.py
RUN wget -O /opt/run.py https://raw.githubusercontent.com/hoptical/nodegraph-api-plugin/main/example/api/python/run.py

RUN /usr/local/bin/pip install flask

EXPOSE 5000

CMD /usr/local/bin/python /opt/run.py
