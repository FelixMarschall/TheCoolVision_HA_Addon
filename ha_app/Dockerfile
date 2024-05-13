# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM

RUN apt-get update && apt-get upgrade -y

# Install requirements for add-on
RUN apt-get install -y \
    python3 \
    python3-pip \
    python3-opencv \
    python3-dev \
    libopencv-dev \
    build-essential \
    cmake \
    libssl-dev \
    tree
# Python 3 HTTP Server serves the current working dir
# So let's set it to our add-on persistent data directory.
WORKDIR /data

COPY thecoolvision/app /data/

RUN pip install -r /data/requirements.txt

RUN pwd

RUN tree

# Start the application
CMD [ "python3", "main.py"]