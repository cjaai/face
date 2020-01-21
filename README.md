"# face" 
Face Detection <br/>
# STEP1
Download FDDB Dataset http://vis-www.cs.umass.edu/fddb/index.html <br/>
Download to D:\face\FDDB <br/>
Folder structure: <br/>
FDDB-folds <br/>
    FDDB-fold-01.txt <br/>
    FDDB-fold-01-ellipseList.txt <br/>
    FDDB-fold-02.txt <br/>
    FDDB-fold-02-ellipseList.txt <br/>
2003  <br/>
jpg files <br/>
2002 <br/>
jpg files <br/>

# STEP2
Run annotation_fddb_darknet.py to get the following <br/>
D:\face\FDDB\FDDB-folds\annotations_darknet  <br/>
1.jpg <br/>
1.txt <br/>
2.jpg <br/>
2.txt <br/>

# STEP3
Copy all .jpg .txt files to D:\darknet\build\darknet\x64\faceData\JPEGImages

# STEP4
All config data is saved in the following folder:<br/>
D:\darknet\build\darknet\x64\faceData

# STEP5
## Training 
```
darknet detector train faceData/face.data faceData/yolov3-face.cfg darknet53.conv.74
```

## Test a picture
```
darknet detector test faceData/face.data faceData/yolov3-face.cfg faceData/backup/yolov3-face_last.weights -thresh 0.65 faceData/JPEGImages/2.jpg
```

## test list
```
darknet detector test faceData/face.data faceData/yolov3-face.cfg faceData/backup/yolov3-face_last.weights -thresh 0.65 < D:\darknet\build\darknet\x64\faceData\test.txt -i 0  > D:\darknet\build\darknet\x64\faceData\result.txt
```
## test video
```
darknet detector demo faceData/face.data faceData/yolov3-face.cfg faceData/backup/yolov3-face_last.weights -thresh 0.65 faceData/JPEGImages/1.mp4 > D:\darknet\build\darknet\x64\faceData\result.txt
```
