FROM python:3.12

ENV PATH="/scripts:${PATH}"

COPY ./requirements.txt /requirements.txt
# RUN apk add --update --no-cache --virtual .tmp gcc libc-dev linux-headers
RUN pip install -r /requirements.txt
# RUN apk del .tmp

RUN mkdir /app
COPY ./crm /app
WORKDIR /app
COPY ./scripts /scripts

RUN chmod +x /scripts/*

RUN mkdir -p /vol/web/media
RUN mkdir -p /vol/web/

RUN adduser user
RUN chown -R user:user /vol
RUN chmod -R 755 /vol/web
USER user

CMD ["entrypoint.sh"]