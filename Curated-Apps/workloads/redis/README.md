# Gramine Curated Redis
In the following two sections, we explain how a Docker image for the protected Redis version can be
built and how the image can be executed.
[Prerequisites](https://github.com/gramineproject/contrib/tree/master/Curated-Apps/README.md) for
both the phases are assumed to be met.

## Build a confidential compute image for Redis
Execute the below commands on the VM.

1. Clone the Gramine Contrib repository:

       $ git clone --depth 1 https://github.com/gramineproject/contrib.git

2. Move to the Curated-Apps folder:

       $ cd contrib/Curated-Apps

3. To generate a preconfigured confidential compute image for Redis, execute the following script:

       $ python3 ./curate.py redis redis:7.0.0 test

4. To generate a custom confidential compute image based on a user-provided Redis image, execute
   the following to launch an interactive setup script:

       $ python3 ./curate.py redis <your_image>

## Run the confidential compute image for Redis

- This example was tested on a Standard_DC2s_v2 Azure VM.
- Follow the output of the image build script `curate.py` to run the generated Docker image.

## Contents
This sub-directory contains artifacts which help in creating curated GSC Redis image, as explained
below:

    .
    |-- redis-gsc.dockerfile.template      # Template used by `curation_script.sh` to create a
    |                                        wrapper dockerfile `redis-gsc.dockerfile` that
    |                                        includes user-provided inputs such as `ca.cert`
    |                                        file and command-line arguments into the graminized
    |                                        Redis image.
    |-- redis.manifest.template            # Template used by `curation_script.sh` to create a
    |                                        user manifest file (with basic set of values defined
    |                                        for graminizing Redis images), that will be passed to
    |                                        GSC.
