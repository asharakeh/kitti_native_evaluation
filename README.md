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

1. `cmake ./`
2. `make`

#### Usage:
Run the evalutaion by:

    ./evaluate_object_3d_offline groundtruth_dir result_dir
    
Note that you don't have to detect over all KITTI training data. The evaluator only evaluates samples whose result files exist.

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
