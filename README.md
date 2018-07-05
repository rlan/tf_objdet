# Object Detection API of TensorFlow

This document describes procedures to install [1]. There are roughly 2 stages:

1. A companion docker image, which already contains all the software 
dependencies.
2. From inside the docker image, prepared a local code folder, which will be 
mounted into the docker image each time you want to run this API.

## Steps

1. Pull the docker image:

`docker pull wqael/tf_objdet:gpu`

2. Download the tensorflow/model project: https://github.com/tensorflow/models
3. Mount the `models` folder into the docker image.

`docker run -it -v ~/models:/notebooks wqael/tf_objdet:gpu bash`

4. From here on, execute from inside docker's bash, e.g.,

```sh
# cd /notebooks/models/
# ls
AUTHORS  CODEOWNERS  CONTRIBUTING.md  ISSUE_TEMPLATE.md  LICENSE  README.md  WORKSPACE  official  research  samples  tutorials
```

5. Follow the COCO API installation in [1]
6. Follow the Protobuf compilation in [1]
7. Add Libraries to PYTHONPATH as [1]
8. "Testing the Installation" as [1]

Installatoin done. From now on, start from step 3 whenever you want to run the API.


[1] https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/installation.md
