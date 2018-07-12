# Object Detection API of TensorFlow

This document describes procedures to install and run [1] with a companion docker image. The companion docker image contains all the software dependencies. For runtime, repo of [1] sits on the host system and is mounted into the docker image.

[1] https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/installation.md


## Installation

1. Pull the docker image. [Dockerfile](docker-gpu/Dockerfile).

```sh
docker pull wqael/tf_objdet:gpu
```

[![](https://images.microbadger.com/badges/image/wqael/tf_objdet:gpu.svg)](https://microbadger.com/images/wqael/tf_objdet:gpu)
[![](https://images.microbadger.com/badges/commit/wqael/tf_objdet:gpu.svg)](https://microbadger.com/images/wqael/tf_objdet:gpu)
![](https://img.shields.io/docker/automated/wqael/tf_objdet.svg)
![](https://img.shields.io/docker/build/wqael/tf_objdet.svg)

2. Download the tensorflow/model project: https://github.com/tensorflow/models
3. Mount the `models` folder into the docker image.

```
docker run -it -p 8888:8888 -p 6006:6006 -v ~/models:/notebooks wqael/tf_objdet:gpu bash
```

4. From here on, execute from inside docker's bash, e.g.,

```
# cd /notebooks/
# ls
AUTHORS  CODEOWNERS  CONTRIBUTING.md  ISSUE_TEMPLATE.md  LICENSE  README.md  WORKSPACE  official  research  samples  tutorials
```

5. Follow the COCO API installation in [1]
6. Follow the Protobuf compilation in [1]
7. Add Libraries to PYTHONPATH as [1]
8. "Testing the Installation" as [1]


## Run-time

1. Mount the `models` folder into the docker image.

```
docker run -it -p 8888:8888 -p 6006:6006 -v ~/models:/notebooks wqael/tf_objdet:gpu bash
```

4. From here on, execute from inside docker's bash, e.g.,

```
cd /notebooks/research
# From tensorflow/models/research/
export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim
```

5. (Optional) Launch jupyter

```
cd /notebooks
jupyter notebook --allow-root
```
