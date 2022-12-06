# Writeup: Track 3D-Objects Over Time

Step 1: Compute Lidar Point-Cloud from Range Image
- Visualize range image channels (ID_S1_EX1): to do this we will need:
  - extract lidar data and range image 
  - extract the range and the intensity channel from the range image
  - convert range and intensity to 8 bit channel
  - stack the range and intensity image vertically
  - change the config in `loop_over_dataset.py`

  The result: <br>
![Image_range](images/range_image.png)
- Visualize lidar point-cloud (ID_S1_EX2)
  - Visualize lidar point-cloud using Open3D

  **Rear-bumper and tail-lights are stable features. In some specific cases, we can see car's front-lights and the wheel as the stable features**
  
  10 samples of the point cloud:

  ![pcl_sample](images/Picture1.png)

  ![pcl_sample](images/Picture2.png)

  ![pcl_sample](images/Picture3.png)

  ![pcl_sample](images/Picture4.png)

  ![pcl_sample](images/Picture5.png)

  ![pcl_sample](images/Picture6.png)

  ![pcl_sample](images/Picture7.png)

  ![pcl_sample](images/Picture8.png)

  ![pcl_sample](images/Picture9.png)

  ![pcl_sample](images/Picture10.png)


Step 2: Creaate BEV from Lidar PCL
- Convert sensor coordinates to BEV-map coordinates (ID_S2_EX1)
  - compute bev-map discretization
  - create a copy of the lidar pcl and transform all metrix x-coordinates into bev-image coordinates
  - perform the same operation as in step 2 for the y-coordinates

  BEV sample:

  ![bev](images/bev.png)

  BEV with intensity

  ![bev_intensity](images/bev_intensity.png)

Step 3 : Model-based Object Detection in BEV Image
- Add a second model from a GitHub repo (ID_S3_EX1)
  - modify the code to load the fpn_resnet model
- Extract 3D bounding boxes from model response (ID_S3_EX2)
  - perform the conversion using the limits for x, y and z set in the configs structure for each detection

  The result:

  ![labelimages](images/label_in_images.png)

  ![labelbev](images/label_in_bev.png)

Step 4 : Performance Evaluation for Object Detection
- Compute intersection-over-union between labels and detections (ID_S4_EX1)

  ![iou](images/iou.png)
- Compute false-negatives and false-positives (ID_S4_EX2)
  
  ![fp](images/fp_fn.png)
  
- Compute precision and recall (ID_S4_EX3)

  ![pr](images/precision_recall.png)

  The result

  ![performance](images/performance.png)
