# Traffic Light Detection.
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

This section was created using this [repository](https://github.com/smasoudn/traffic_light_detection/blob/master/create_udacity_tf_record.py) as reference:

The [tf_record.py](./tf_record.py) file `was modified` in order to fix deprecated code lines.**

**To be considered:**

### 1. Downloads :

The itens where is nessary download files ( e.g. itens 2,6,etc) are not availabe in this repository, You must download from the links availables [here](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg) in order to run locally.

### 2. record files:

Below the item 5 runned locally and the .record files generated.

<p align="center">
  <img src="images/record files.jpg">
</p>

For details about the process, individual information is here: [real](./images/real_record.jpg) and "[simulator](./images/sim_record.jpg)

### 3. Pretrained Model:

It was chosen the [ssd_mobilenet_V2_coco](http://download.tensorflow.org/models/object_detection/ssd_mobilenet_v2_coco_2018_03_29.tar.gz).The main reason is the performance about how faster this module runs compared with others.

### 4. Config file:

Here is the link for [ssd_mobilenet_v2_coco.config](https://github.com/tensorflow/models/blob/master/research/object_detection/samples/configs/ssd_mobilenet_v2_coco.config) file.

The `fine_tune_checkpoint` are:

- line 9: Modified value from 90 to 4.
- line 41: Inserted line "reduce_boxes_in_lowest_layer: true".
- line 134: Modified value from 100 to 50. 
- line 135: Modified value from 100 to 50. 
- line 164: Modified value from 200000 to 10000. 
- line 177: Inserted path to .record file.
- line 179: Inserted path to .pbtxt file

- Commented lines from 182 to 196.

It was created 2 .config file, the diference is the path for the .record file at line 177, more detail could be checked here [real](./training/Real/ssd_mobilenet_v2_coco.config) and [Simulator](./training/Simulator/ssd_mobilenet_v2_coco.config).<br/>
PS: The file name is the same.

### 5. pbtxt file:

The File contain the id number associated to a traffic light color:

- id 1: Green.
- id 2: Red.
- id 3: Yellow.
- id 4: Unknown.

For more detail, please check the [label_map.pbtxt](./training/label_map.pbtxt) file.

### 6. Training the model. 

this command line used in `tensorflow models/research/`

- For Real:<br/>
```
python train.py  --logtostderr --train_dir=training/ --pipeline_config_path=training/Real/ssd_inception_v2_coco.config
```

- For Simulator:<br/>

```
python3 train.py  --logtostderr --train_dir=training/ --pipeline_config_path=training/Simulator/ssd_inception_v2_coco.config
```
