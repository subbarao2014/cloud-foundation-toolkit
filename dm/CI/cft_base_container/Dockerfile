FROM gcr.io/google.com/cloudsdktool/cloud-sdk 
# gcr.io/cloud-builders/gcloud

RUN set -ex && apt-get update && apt-get -y install make \
    && apt-get -y install gettext-base \
    && python3 --version \
    && pip3 install --upgrade pip \
    && pip3 --version \
    && pip3 install setuptools \
    && git clone https://github.com/GoogleCloudPlatform/cloud-foundation-toolkit \
    && cd cloud-foundation-toolkit/dm \
    && rm -rf templates \
    && pip3 install tox \
    && pip3 install pytest wheel \
    && make build \
    && make install \
    && make cft-venv \
    && make template-prerequisites \
    && make cft-prerequisites \
    && . venv/bin/activate \
    && ./src/cftenv \
    && pwd \
    && cft --version \
    && bats -v \
    && which bats

WORKDIR /cloud-foundation-toolkit/dm
