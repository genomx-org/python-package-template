FROM mcr.microsoft.com/devcontainers/python:3

RUN python -m pip install --upgrade pip \
    && python -m pip install 'flit>=3.8.0'

ENV FLIT_ROOT_INSTALL=1

COPY pyproject.toml .
COPY requirements.txt /tmp/pip-tmp/

RUN pip3 --disable-pip-version-check --no-cache-dir install -r /tmp/pip-tmp/requirements.txt \
    && rm -rf /tmp/pip-tmp
RUN touch README.md \
    && mkdir -p src/python_package \
    && python -m flit install --only-deps --deps develop \
    && rm -r pyproject.toml README.md src
