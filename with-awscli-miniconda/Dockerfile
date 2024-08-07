FROM amazonlinux:2

ENV MINICONDA_PATH=~/miniconda
ENV PYTHON_VERSION=3.12
ENV PYTHON_ENV_NAME=py312

# yum update & install
RUN yum update -y
RUN yum install -y sudo unzip

# install AWS-CLI V2
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "aws_cli_v2.zip"
RUN unzip aws_cli_v2.zip
RUN sudo ./aws/install
RUN rm aws_cli_v2.zip

# install miniconda
RUN mkdir -p ${MINICONDA_PATH}
RUN curl https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -o ${MINICONDA_PATH}/miniconda.sh
RUN bash ${MINICONDA_PATH}/miniconda.sh -b -u -p ${MINICONDA_PATH}
RUN ${MINICONDA_PATH}/bin/conda init bash

# Create python environment
RUN ${MINICONDA_PATH}/bin/conda create -n ${PYTHON_ENV_NAME} python=${PYTHON_VERSION}
RUN echo "conda activate ${PYTHON_ENV_NAME}" >> ~/.bashrc

CMD ["/bin/bash"]