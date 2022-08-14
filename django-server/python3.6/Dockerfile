FROM python:3.10.6-slim-buster

# The enviroment variable ensures that the python output is set straight
# to the terminal with out buffering it first
ENV PYTHONUNBUFFERED 1

# create root directory for the project inside the container
RUN mkdir /src

# Set the working directory to /src
WORKDIR /src

# Install necessary packages
RUN apt-get update && apt-get install -y libpq-dev python3-dev \
&& pip3 install --upgrade pip \
&& rm -rf /var/lib/apt/lists/*

# Copy the current directory contents into the container at /tmp
ADD requirements.txt /tmp

# Install any needed packages specified in requirements.txt
RUN pip3 install -r /tmp/requirements.txt

EXPOSE 8000

CMD [ "sh", "-c", "python manage.py runserver 0.0.0.0:8000" ]