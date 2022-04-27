# CVAT UTILS
Utilities for CVAT

# COCO JSON to CVAT XML

Converts COCO JSON to CVAT XML.

## Usage

```bash
usage: coco2cvatxml.py [-h] --coco FILE --cvat-xml FILE 

positional arguments:
  coco             Path to COCO JSON
  cvat-xml         Path to CVAT XML

```

## Examples

```bash
python coco2cvatxml.py --coco task_1.json --cvat-xml annotations.xml
```

# CVAT XML to COCO JSON

Converts CVAT XML to COCO JSON.

## Usage

```bash
usage: cvatxml2coco.py [-h] --cvat-xml FILE [--image-dir DIRECTORY] --coco FILE

positional arguments:
  cvat-xml          Path to CVAT XML
  coco              Path to COCO JSON
  image-dir         Path to images root directory (optional)

```

## Examples

```bash
python cvatxml2coco.py --cvat-xml annotations.xml --coco out.json --image-dir \images\
```

# The Annotations

## key points person
There are 17 key points.
![image](https://user-images.githubusercontent.com/35894891/165474348-1b7f7082-37db-4ff9-8cf8-0b5d3130565a.png)

## COCO JSON
The annotation json file is in the format of MSCOCO dataset. You can use pycoco tools to read the annotations.
There is one annotation file for one video which contains the annotations from the frames in the video. 

For the person we have the following annotations:<br />
```bash
annotation{
  "id"           : int, → Each annotation also has an id (unique to all other annotations)
  "bbox"         : [x,y,width,height], → Denoting the bbox location of that person. Box coordinates are measured from the top left image corner and are 0-indexed
  "keypoints"    : [x1,y1,v1,x2,y2,v2...], → x and y indicate pixel positions in the image. v indicates visibility— v=0: not labeled (in which case x=y=0), v=1: labeled but not visible, and v=2: labeled and visible 
  "track_id"    : int, → The tracking ID of the individual, This ID remains constant for that person/object in all the sequences of the video
  "image_id"    : int, 
  "frame_id"    : int, → The frame id of this frame in the video
  "activity"    : [action1,action2...] → The person's actions which are captured  
  "category_id" :1 → This ID 1 is for Human.
}

categories[{
  supercategory": "person",
  "id": 1,
  "name": "person",
  "keypoints": ["nose","head_bottom","head_top","left_ear","right_ear","left_shoulder","right_shoulder","left_elbow","right_elbow","left_wrist","right_wrist","left_hip","right_hip","left_knee","right_knee","left_ankle","right_ankle"], 
  "skeleton": [16,14],[14,12],[17,15],[15,13],[12,13],[6,12],[7,13],[6,7],[6,8],[7,9],[8,10],[9,11],[2,3],[1,2],[1,3],[2,4],[3,5],[4,6],[5,7], → defines connectivity  via a list of keypoint edge pairs 
}]
```


