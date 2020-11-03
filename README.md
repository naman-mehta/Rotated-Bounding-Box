# Rotated-Bounding-Box
Detect rotated or oriented bounding boxes

Few methods that can be used for detecting rotated bounding boxes.

1-Regress BBox and an angle which decribe the rotation of the box.

2-Directly regression the 4 points as a polygon of the shape. these method have Centernet Cornernet etc

3-Use existing object segmentation techniques like MaskRCNN and and then PCA to generate oriented object detection for reference [link](https://hewjunwei.wordpress.com/2013/01/26/obb-generation-via-principal-component-analysis/)

3rd approach is too slow and 1st approach seems not easy to read desired accuracy.

A quick workaround can be to use common object detection and then segmentation only on object detected.
For this one can easily pick 2 successfull models.
Deep Extreme Cut or [dextr](http://www.vision.ee.ethz.ch/~cvlsegmentation/dextr/). DEXTR is extreme point guided image segmentation method. 
Have already used it in CVAT. It needs like 2 or 3 corner points as input and can perform object segmentation very fast and acurate.
To complement dextr cornernet can be used as while regressing corners it also do corner pooling. Local maxima from these can be very useful as an input to dextr.

Currently there is a model which tries to do the same called [ExtremeNet](https://github.com/xingyizhou/ExtremeNet) from the owners of centrenet.

Based on 2nd approach there is a model Super-Fast-Accurate-3D-Object-Detection-PyTorch [SFA3d](https://github.com/maudzung/SFA3D) which has adopted CenterNet ideas for the rotated boxes detection task.
It predicts 3d bounding box through regression and can be used to regress rotated bounding box.


