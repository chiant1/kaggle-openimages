
## Object Detection
### Export Frozen Graph
~~~~
python object_detection/export_inference_graph.py \
  -input_type image_tensor \
  --pipeline_config_path ./object_detection/samples/configs/faster_rcnn_inception_resnet_v2_atrous_oid_v2.config \
  --trained_checkpoint_prefix ~/openimages/model_zoo/faster_rcnn_inception_resnet_v2_atrous_oid_2018_01_28_v2/model.ckpt \
  --output_directory v2
~~~~
