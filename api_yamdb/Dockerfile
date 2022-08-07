FROM python:3.7-slim

RUN mkdir /my_app

COPY requirements.txt /my_app

RUN pip3 install -r /my_app/requirements.txt --no-cache-dir

COPY . /my_app

WORKDIR /my_app

CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ]
