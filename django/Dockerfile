# pull official base image
FROM python:3.7

# set work directory
WORKDIR /usr/src/django

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install psycopg2 dependencies
RUN apt-get update && apt-get install -y \
  netcat \
  binutils \
  libproj-dev \
  gdal-bin \
  postgresql-client \
  && pip install virtualenv \
  && mkdir /code/

# install dependencies
RUN pip install --upgrade pip wheel
COPY ./requirements.txt .
RUN pip install -r requirements.txt

# copy entrypoint.sh
COPY ./entrypoint.sh .

# copy project
COPY . .

# run entrypoint.sh
ENTRYPOINT ["/usr/src/django/entrypoint.sh"]

