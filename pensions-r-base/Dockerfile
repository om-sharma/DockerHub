FROM r-base
RUN apt-get update && apt-get install -y --no-install-recommends \
        libcurl4 \
        libcurl4-openssl-dev \
        libssl-dev \
        libxml2-dev \
        r-base-core \
        r-cran-littler \
        jq \
        openjdk-8-jdk \
        python-setuptools \
        python-pip

RUN pip install awscli

# install base packages
RUN Rscript -e "install.packages(\"glue\", dependencies=TRUE)"
RUN Rscript -e "install.packages(\"dplyr\", dependencies=TRUE)"
RUN Rscript -e "install.packages(\"stringi\", dependencies=TRUE)"
RUN install.r lubridate remotes curl openssl httr xml2 base64enc stringr data.table


# install AWS packages : used to read data directly from and write data directly to S3
RUN Rscript -e "install.packages(\"aws.signature\", repos = c(cloudyr = \"http://cloudyr.github.io/drat\", getOption(\"repos\")))"
RUN Rscript -e "install.packages(\"aws.ec2metadata\", repos = c(cloudyr = \"http://cloudyr.github.io/drat\", getOption(\"repos\")))"
RUN Rscript -e "install.packages(\"aws.s3\", repos = c(\"cloudyr\" = \"http://cloudyr.github.io/drat\"))"

