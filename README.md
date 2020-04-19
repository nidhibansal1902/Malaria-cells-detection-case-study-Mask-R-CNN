# Malaria-cells-detection-case-study-Mask-R-CNN
It is based on Computer vision. Object detection is implemented using Mask-RCNN
Malaria cell detection- Bounding Box Case Study
In this case study Images are in .png or .jpg format. There are 2 sets of images consisting of 1208
training and 120 test images.
Labels: The data consists of two classes of uninfected cells (RBCs and leukocytes) and four
classes of infected cells (gametocytes, rings, trophozoites, and schizonts). Annotators were permitted to mark some cells as difficult if not clearly in one of the cell classes. The data had a heavy
imbalance towards uninfected RBCs versus uninfected leukocytes and infected cells, making up
over 95% of all cells.
A class label and set of bounding box coordinates were given for each cell.
2 Problem Statement
This case study is based on Computer Vision. Here, we will use Image segmentation technique.
and we will do Object identification + instance segmentation.
Image segmentation creates a pixel-wise mask for each object in the image. This technique
gives us a far more granular understanding of the object in the image.
Task is to identify Malaria cells of each image if they are uninfected cells (RBCs and leukocytes)
and four classes of infected cells (gametocytes, rings, trophozoites, and schizonts)
3 Approach
I will train model using Mask-RCNN (Mask Regional Convolutional Neural Network).
I have learnt Mask-RCNN from the below link. It is training Kangaroo object detection dataset. Some code snippents are taken from the below reference link. #Ref:
https://machinelearningmastery.com/how-to-train-an-object-detection-model-with-keras/
Mask_RCNN gives 3 outputs: 1. Class_ids with Prediction score 2. Objects/Cells Bounding
Box 3. Mask for Objects/Cells
4 Evaluation Metrics
4.0.1 mAP: Mean Average Precision
The performance of a model for an object recognition task is often evaluated using the mAP and
IOU. We are predicting bounding boxes so we can determine how well the predicted and actual
1
bounding boxes overlap. This can be calculated by dividing the area of the overlap by the total
area of both bounding boxes, or the intersection divided by the union, referred to as “intersection
over union,” or IoU. A perfect bounding box prediction will have an IoU of 1. It is standard to
assume a positive prediction of a bounding box if the IoU is greater than 0.5, e.g. they overlap by
50% or more.
Precision refers to the percentage of the correctly predicted bounding boxes (IoU > 0.5) out
of all bounding boxes predicted in the image. Recall is the percentage of the correctly predicted
bounding boxes (IoU > 0.5) out of all objects in the image. As we make more predictions, the recall
percentage will increase, but precision will drop or become erratic as we start making false positive
predictions. The recall (x) can be plotted against the precision (y) for each number of predictions
to create a curve or line. We can maximize the value of each point on this line and calculate the
average value of the precision or AP for each value of recall. The average or mean of the average
precision (AP) across all of the images in a dataset is called the mean average precision, or mAP.
The mask-rcnn library provides a mrcnn.utils.compute_ap to calculate the AP and other metrics for a given images. These AP scores can be collected across a dataset and the mean calculated
to give an idea at how good the model is at detecting objects in a dataset.
