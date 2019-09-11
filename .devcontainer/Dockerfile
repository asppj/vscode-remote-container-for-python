#-------------------------------------------------------------------------------------------------------------
# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License. See https://go.microsoft.com/fwlink/?linkid=2090316 for license information.
#-------------------------------------------------------------------------------------------------------------

FROM python:3.7

ENV PYTHONUNBUFFERED 1

# COPY ["./sources.list /etc/apt/sources.list","./pip.ini ~/.pip/pip.conf","./requirements.txt requirements.txt* /workspace/"]
COPY ./sources.list /etc/apt/sources.list
COPY ./pip.ini ~/.pip/pip.conf
COPY ./requirements.txt requirements.txt* /workspace/

# WORKDIR /workspace

# Install Python dependencies from requirements.txt if it exists
RUN if [ -f "requirements.txt" ]; then pip install -r requirements.txt && rm requirements.txt; fi \
    && apt-get update && apt-get -y install git procps lsb-release

# Clean up
RUN apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*

# Set the default shell to bash instead of sh
ENV SHELL /bin/bash
