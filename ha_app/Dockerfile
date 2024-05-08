# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM

# Install requirements for add-on
RUN \
  apk add --no-cache \
    python3 \
    py3-pip \
    python3-dev \
    python-opencv \
    build-base \
    cmake

# Python 3 HTTP Server serves the current working dir
# So let's set it to our add-on persistent data directory.
WORKDIR /data

COPY thecoolvision/app /data/

RUN \
  pip install -r /data/requirements.txt

# Start the application
CMD [ "python3", "main.py"]