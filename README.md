# kitti_native_evaluation

This code is based on Bo Li's repository: https://github.com/prclibo/kitti_eval with the main differences being some code cleanup and
 additional AHS metric described in our paper: [Joint 3D Proposal Generation and Object Detection from View Aggregation
                                               ](https://arxiv.org/abs/1712.02294)

`evaluate_object_3d_offline.cpp` evaluates your KITTI detection locally on 
your own computer using your validation data selected from KITTI training dataset, with the following metrics:

- overlap on image (AP)
- oriented overlap on image (AOS)
- overlap on ground-plane (AP)
- oriented overlap on ground-plane (AHS)
- overlap in 3D (AP)
- oriented overlap in 3D (3D AHS)

#### Compilation:
Clone the repo using: 
`git clone https://github.com/asharakeh/kitti_native_evaluation.git`

From inside the main folder do:
1. `cmake ./`
2. `make`

#### Usage:
Run the evalutaion by:

    ./evaluate_object_3d_offline groundtruth_dir result_dir
    
Note that you don't have to detect over all KITTI training data. The evaluator only evaluates samples whose result files exist.

## Data Format:
The detection format should be simillar to the KITTI dataset label format with 15 columns representing:

#Values    Name      Description
----------------------------------------------------------------------------
   1    type         Describes the type of object: 'Car', 'Van', 'Truck',
                     'Pedestrian', 'Person_sitting', 'Cyclist', 'Tram',
                     'Misc' or 'DontCare'
   1    truncated    Float from 0 (non-truncated) to 1 (truncated), where
                     truncated refers to the object leaving image boundaries
   1    occluded     Integer (0,1,2,3) indicating occlusion state:
                     0 = fully visible, 1 = partly occluded
                     2 = largely occluded, 3 = unknown
   1    alpha        Observation angle of object, ranging [-pi..pi]
   4    bbox         2D bounding box of object in the image (0-based index):
                     contains left, top, right, bottom pixel coordinates
   3    dimensions   3D object dimensions: height, width, length (in meters)
   3    location     3D object location x,y,z in camera coordinates (in meters)
   1    rotation_y   Rotation ry around Y-axis in camera coordinates [-pi..pi]
   1    score        Only for results: Float, indicating confidence in
                     detection, needed for p/r curves, higher is better.

Here, 'DontCare' labels denote regions in which objects have not been labeled,
for example because they have been too far away from the laser scanner. To
prevent such objects from being counted as false positives our evaluation
script will ignore objects detected in don't care regions of the test set.
You can use the don't care labels in the training set to avoid that your object
detector is harvesting hard negatives from those areas, in case you consider
non-object regions from the training images as negative examples.


## Citation:
If you are using this code, please cite our paper:

[Joint 3D Proposal Generation and Object Detection from View Aggregation
](https://arxiv.org/abs/1712.02294)


`@article{ku2017joint,
  title={Joint 3D Proposal Generation and Object Detection from View Aggregation},
  author={Ku, Jason and Mozifian, Melissa and Lee, Jungwook and Harakeh, Ali and Waslander, Steven},
  journal={arXiv preprint arXiv:1712.02294},
  year={2017}
}`
