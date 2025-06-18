FROM python:3.10-slim
LABEL maintainer="jeep.jipu@gmail.com" version="1.0"
WORKDIR /root/

RUN pip install beancount fava

RUN mkdir /root/beancount

EXPOSE 5001
CMD fava beancount/moneybook.bean --host 0.0.0.0 --port 5001
