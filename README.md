"# face" 
Face Detection
# STEP1
Download FDDB Dataset http://vis-www.cs.umass.edu/fddb/index.html
Download to D:\face\FDDB
Folder structure:
FDDB-folds
    FDDB-fold-01.txt
    FDDB-fold-01-ellipseList.txt
    FDDB-fold-02.txt
    FDDB-fold-02-ellipseList.txt
2003 
jpg files
2002 
jpg files

# STEP2
Run annotation_fddb_darknet.py to get the following
D:\face\FDDB\FDDB-folds\annotations_darknet 
1.jpg
1.txt
2.jpg
2.txt

# STEP3
Copy all .jpg .txt files to D:\darknet\build\darknet\x64\faceData\JPEGImages

# STEP4
All config data is saved in the following folder:
D:\darknet\build\darknet\x64\faceData

# STEP5
## Training 
darknet detector train faceData/face.data faceData/yolov3-face.cfg darknet53.conv.74

## Test a picture
darknet detector test faceData/face.data faceData/yolov3-face.cfg faceData/backup/yolov3-face_last.weights -thresh 0.65 faceData/JPEGImages/2.jpg

## test list
darknet detector test faceData/face.data faceData/yolov3-face.cfg faceData/backup/yolov3-face_last.weights -thresh 0.65 < D:\darknet\build\darknet\x64\faceData\test.txt -i 0  > D:\darknet\build\darknet\x64\faceData\result.txt

## test video
```
darknet detector demo faceData/face.data faceData/yolov3-face.cfg faceData/backup/yolov3-face_last.weights -thresh 0.65 faceData/JPEGImages/1.mp4 > D:\darknet\build\darknet\x64\faceData\result.txt
```
