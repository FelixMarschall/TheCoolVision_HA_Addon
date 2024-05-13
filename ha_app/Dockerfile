# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM

# Execute during the build of the image
ARG TEMPIO_VERSION BUILD_ARCH
RUN \
    curl -sSLf -o /usr/bin/tempio \
    "https://github.com/home-assistant/tempio/releases/download/${TEMPIO_VERSION}/tempio_${BUILD_ARCH}"

# Install requirements for add-on
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y \
    python3 \
    python3-pip \
    python3-opencv \
    python3-dev \
    libopencv-dev \
    build-essential \
    cmake \
    libssl-dev \
    tree \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app_data

COPY run.sh /app_data/
COPY thecoolvision/app /app_data/

RUN pip install -r /app_data/requirements.txt

RUN chmod a+x ./run.sh
CMD [ "./run.sh" ]