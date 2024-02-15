Commands to run (ensure that you have tao_experiments folder)

export DOCKER_REGISTRY="nvcr.io"
export DOCKER_NAME="nvidia/tao/tao-toolkit"
export DOCKER_TAG="5.0.0-tf1.15.5" ## for TensorFlow docker
export DOCKER_CONTAINER=$DOCKER_REGISTRY/$DOCKER_NAME:$DOCKER_TAG
docker run -it --rm --gpus all -v /home/tarun/Desktop/tao_experiments/:/workspace/tao-experiments $DOCKER_CONTAINER "if docker image is not present, it will download"
cd tao-experiments/
classification_tf1 train -e classification_tf1/classification_spec.cfg  -r classification_tf1/output -k nvidia_tlt --gpus 1
"You will see that each epoch will start, train data and paths have to be manage in classification_spec.cfg file"
