.. _installation:

Installation
============

1. Clone the repository

::
    
    git clone git@github.com:haniffalab/webatlas-pipeline.git
    cd webatlas-pipeline
    
2. Install nextflow by following the `documentation`_
3. Install `Docker`_ and make sure it's in :code:`PATH`
4. Build the docker images.

:: 

    cd docker
    ./build-docker-imgs.sh

.. _documentation: https://www.nextflow.io/index.html#GetStarted
.. _Docker: https://docs.docker.com/engine/install/

