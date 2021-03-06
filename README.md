# UDP-Pose
 Official code of 《The Devil is in the Details: Delving into Unbiased Data Processing for Human Pose Estimation》
 
 ![Illustrating the performance of the proposed UDP](/figures/UDP.png)
 
## News
* \[2019/11/7\] UDP is now on [ArXiv](https://arxiv.org/abs/1911.07524).
* \[2019/11/10\] [Project page](https://github.com/HuangJunJie2017/UDP-Pose) is created.
* \[2019/12/7\] Further research promotes the UPD to UDP-v1 which can help the small backbone HRNet-w32-256x192 scoring **77.2AP** on **COCO val** and **75.4AP** on **COCO test-dev**!
* \[2020/2/21\] We reproduct UDP-v1 on mxnet which can help the small backbone HRNet-w32-256x192 scoring **78.1AP** on **COCO val** with groundtruth boxes **77.3AP** on **COCO val** with detecting boxes and **75.5AP** on **COCO test-dev**.
* \[2020/2/24\] Paper has been accepted by CVPR2020!

# Main Results
### Results on MPII val dataset
|Method---|Head|Sho.|Elb.|Wri.|Hip|Kne.|Ank.|Mean|Mean 0.1|
|---------|----|----|----|----|----|----|----|----|----|
|HRNet32  |97.1|95.9|90.3|86.5|89.1|87.1|83.3|90.3|37.7|
|+Dark    |97.2|95.9|91.2|86.7|89.7|86.7|84.0|90.6|42.0|
|+Dark+UDP|97.4|96.0|91.0|86.5|89.1|86.6|83.3|90.4|42.1|
### Results on COCO val2017 with detector having human AP of 65.1 on COCO val2017 dataset
| Arch            | Input size | #Params | GFLOPs |   AP | Ap .5 | AP .75 | AP (M) | AP (L) |    AR |
|-----------------|------------|---------|--------|------|-------|--------|--------|--------|-------|
| pose_resnet_50  |    256x192 | 34.0M   |   8.90 | 71.3 | 89.9  |  78.9  |  68.3  |  77.4  | 76.9  |
| **+UDP**        |    256x192 | 34.2M   |   8.96 | 72.9 | 90.0  |  80.2  |  69.7  |  79.3  | 78.2  |
| pose_resnet_50  |    384x288 | 34.0M   |   20.0 | 73.2 | 90.7  |  79.9  |  69.4  |  80.1  | 78.2  |
| **+UDP**        |    384x288 | 34.2M   |   20.1 | 74.0 | 90.3  |  80.0  |  70.2  |  81.0  | 79.0  |
| pose_resnet_152 |    256x192 | 68.6M   |   15.7 | 72.9 | 90.6  |  80.8  |  69.9  |  79.0  | 78.3  |
| **+UDP**        |    256x192 | 68.8M   |   15.8 | 74.3 | 90.9  |  81.6  |  71.2  |  80.6  | 79.6  |
| pose_resnet_152 |    384x288 | 68.6M   |   35.6 | 75.3 | 91.0  |  82.3  |  71.9  |  82.0  | 80.4  |
| **+UDP**        |    384x288 | 68.8M   |   35.7 | 76.2 | 90.8  |  83.0  |  72.8  |  82.9  | 81.2  |
| pose_hrnet_w32  |    256x192 | 28.5M   |   7.10 | 75.6 | 91.9  |  83.0  |  72.2  |  81.6  | 80.5  |
| **+UDP**        |    256x192 | 28.7M   |   7.16 | 76.8 | 91.9  |  83.7  |  73.1  |  83.3  | 81.6  |
| **+UDP-v1**     |    256x192 | 28.7M   |   7.16 | 77.2 | 91.9  |  84.2  |  74.0  |  83.3  | 82.0  |
| **+UDP-v2**     |    256x192 | 28.7M   |   7.16 | 77.8 | -     | -      |  -     | -      | -     |
| **RSN18+UDP**   |    256x192 | -       |    2.5 | 74.7 | -     | -      |  -     | -      | -     |
| pose_hrnet_w32  |    384x288 | 28.5M   |   16.0 | 76.7 | 91.9  |  83.6  |  73.2  |  83.2  | 81.6  |
| **+UDP**        |    384x288 | 28.7M   |   16.1 | 77.8 | 91.7  |  84.5  |  74.2  |  84.3  | 82.4  |
| pose_hrnet_w48  |    256x192 | 63.6M   |   14.6 | 75.9 | 91.9  |  83.5  |  72.6  |  82.1  | 80.9  |
| **+UDP**        |    256x192 | 63.8M   |   14.7 | 77.2 | 91.8  |  83.7  |  73.8  |  83.7  | 82.0  |
| pose_hrnet_w48  |    384x288 | 63.6M   |   32.9 | 77.1 | 91.8  |  83.8  |  73.5  |  83.5  | 81.8  |
| **+UDP**        |    384x288 | 63.8M   |   33.0 | 77.8 | 92.0  |  84.3  |  74.2  |  84.5  | 82.5  |

### Note:
- Flip test is used.
- Person detector has person AP of 65.1 on COCO val2017 dataset.
- GFLOPs is for convolution and linear layers only.

### Results on COCO test-dev with detector having human AP of 65.1 on COCO val2017 dataset
| Arch            | Input size | #Params | GFLOPs |   AP | Ap .5| AP .75| AP (M)| AP (L)|    AR|
|-----------------|------------|---------|--------|------|------|-------|-------|-------|------|
| pose_resnet_50  |    256x192 | 34.0M   |   8.90 | 70.2 | 90.9 |  78.3 |  67.1 |  75.9 | 75.8 |
| **+UDP**        |    256x192 | 34.2M   |   8.96 | 71.7 | 91.1 |  79.6 |  68.6 |  77.5 | 77.2 |
| pose_resnet_50  |    384x288 | 34.0M   |   20.0 | 71.3 | 91.0 |  78.5 |  67.3 |  77.9 | 76.6 |
| **+UDP**        |    384x288 | 34.2M   |   20.1 | 72.5 | 91.1 |  79.7 |  68.8 |  79.1 | 77.9 |
| pose_resnet_152 |    256x192 | 68.6M   |   15.7 | 71.9 | 91.4 |  80.1 |  68.9 |  77.4 | 77.5 |
| **+UDP**        |    256x192 | 68.8M   |   15.8 | 72.9 | 91.6 |  80.9 |  70.0 |  78.5 | 78.4 |
| pose_resnet_152 |    384x288 | 68.6M   |   35.6 | 73.8 | 91.7 |  81.2 |  70.3 |  80.0 | 79.1 |
| **+UDP**        |    384x288 | 68.8M   |   35.7 | 74.7 | 91.8 |  82.1 |  71.5 |  80.8 | 80.0 |
| pose_hrnet_w32  |    256x192 | 28.5M   |   7.10 | 73.5 | 92.2 |  82.0 |  70.4 |  79.0 | 79.0 |
| **+UDP**        |    256x192 | 28.7M   |   7.16 | 75.2 | 92.4 |  82.9 |  72.0 |  80.8 | 80.4 |
| **+UDP-v1**     |    256x192 | 28.7M   |   7.16 | 75.4 | 92.4 |  82.9 |  72.2 |  81.0 | 80.6 |
| **+UDP-v2**     |    256x192 | 28.7M   |   7.16 | 76.3 | -    |  -    |  -    | -     | -    |
| pose_hrnet_w32  |    384x288 | 28.5M   |   16.0 | 74.9 | 92.5 |  82.8 |  71.3 |  80.9 | 80.1 |
| **+UDP**        |    384x288 | 28.7M   |   16.1 | 76.1 | 92.5 |  83.5 |  72.8 |  82.0 | 81.3 |
| pose_hrnet_w48  |    256x192 | 63.6M   |   14.6 | 74.3 | 92.4 |  82.6 |  71.2 |  79.6 | 79.7 |
| **+UDP**        |    256x192 | 63.8M   |   14.7 | 75.7 | 92.4 |  83.3 |  72.5 |  81.4 | 80.9 |
| pose_hrnet_w48  |    384x288 | 63.6M   |   32.9 | 75.5 | 92.5 |  83.3 |  71.9 |  81.5 | 80.5 |
| **+UDP**        |    384x288 | 63.8M   |   33.0 | 76.5 | 92.7 |  84.0 |  73.0 |  82.4 | 81.6 |
### Note:
- Flip test is used.
- Person detector has person AP of 65.1 on COCO val2017 dataset.
- GFLOPs is for convolution and linear layers only.


# Quick Start
Data preparation
For coco, we providied the human detection result at [BaiduDisk](https://pan.baidu.com/s/1mPuVj8piYzgWjoRgyd0Cwg)(dsa9)


# Compare Offset with DARK 
DARK: a gaussian heatmap based unbiased decoding method《Distribution-Aware Coordinate Representation for Human Pose Estimation》
###val

| method          | Input size | backbone| GFLOPs | boundingbox  |   AP |
|-----------------|------------|---------|--------|--------------|------|
| dark            |    256x192 | r50     |   8.90 | gt           | 73.7 |
| offset          |    256x192 | r50     |   8.96 | gt           | 74.3 |
| dark            |    256x192 | r50     |   8.90 | det          | -    |
| offset          |    256x192 | r50     |   8.96 | det          | 72.9 |
|-----------------|------------|---------|--------|--------------|------|
| dark            |    256x192 | w32     |   7.10 | gt           | 78.1 |
| offset          |    256x192 | w32     |   7.16 | gt           | 78.0 |
| dark            |    256x192 | w32     |   7.10 | det          | 76.8 |
| offset          |    256x192 | w32     |   7.16 | det          | 76.8 |

###test-dev
| method          | Input size | backbone| GFLOPs | boundingbox  |   AP |
|-----------------|------------|---------|--------|--------------|------|
| dark            |    256x192 | w32     |   7.10 | det          | 75.0 |
| offset          |    256x192 | w32     |   7.16 | det          | 75.2 |
| dark*           |    384x288 | w48     |   32.9 | det          | 76.2 |
| offset          |    384x288 | w48     |   33.0 | det          | 76.5 |

*metric from drak project without udp
