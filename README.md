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
The detection format should be the same as KITTI's Ground Truth Text Format with an additional "Score" value at the end of each line.
Example Detection File: 

Pedestrian 0.00 2 0.29 873.70 152.10 933.44 256.07 1.87 0.50 0.90 5.42 1.50 13.43 0.67 0.99\
Car 0.00 0 1.74 444.29 171.04 504.95 225.82 1.86 1.57 3.83 -4.95 1.83 26.64 1.55 0.85\
Pedestrian 0.00 0 -0.39 649.28 168.10 664.61 206.40 1.78 0.53 0.95 2.20 1.57 34.08 -0.33 0.21\

The name of files should correspond to the name of the frame it originated from. As an example: 000000.txt detection file will corresponds to the 000000 frame and will be evaluated using the 000000.txt ground truth. 

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
