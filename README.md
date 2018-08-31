
## Object Detection
### Export Frozen Graph
~~~~
python object_detection/export_inference_graph.py \
  -input_type image_tensor \
  --pipeline_config_path ./object_detection/samples/configs/faster_rcnn_inception_resnet_v2_atrous_oid_v2.config \
  --trained_checkpoint_prefix ~/openimages/model_zoo/faster_rcnn_inception_resnet_v2_atrous_oid_2018_01_28_v2/model.ckpt \
  --output_directory v2
~~~~

### Expand.sh

~~~~
ROOT=./info
HIERARCHY_FILE=${ROOT}/bbox_labels_500_hierarchy.json
BOUNDING_BOXES=${ROOT}/challenge-2018-train-annotations-bbox
IMAGE_LABELS=${ROOT}/challenge-2018-train-annotations-human-imagelabels

export PATH=./tensorflow/models/research:$PATH

python object_detection/dataset_tools/oid_hierarchical_labels_expansion.py \
    --json_hierarchy_file=${HIERARCHY_FILE} \
    --input_annotations=${BOUNDING_BOXES}.csv \
    --output_annotations=${BOUNDING_BOXES}_expanded.csv \
    --annotation_type=1

python object_detection/dataset_tools/oid_hierarchical_labels_expansion.py \
    --json_hierarchy_file=${HIERARCHY_FILE} \
    --input_annotations=${IMAGE_LABELS}.csv \
    --output_annotations=${IMAGE_LABELS}_expanded.csv \
    --annotation_type=2
~~~~
