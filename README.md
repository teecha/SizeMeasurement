# SizeMeasurement

Just clone and run using
```shell

python measure_object_size_camera.py

```

For camera calibration and Aruco tag generation follow the code and documentation available at:
https://github.com/teecha/Aruco_car

Result Image
![alt text](https://github.com/teecha/SizeMeasurement/blob/main/results/ameOutput.png?raw=true)


**Smart Segregation Using Classical Computer Vision**

Computer Vision has gained popularity in the modern world and attracts a lot of

attention thanks to its versatility in a wide range of applications. By incorporating computer

vision technology into the system, the current sorting mechanism in the industrial environment

needs to be upgraded. The sorting procedure is still carried out manually using human labor in

some light businesses. However, this conventional approach has some drawbacks, including the

possibility of human error, sluggish productivity, lack of accuracy, and expensive labor costs.

The aforementioned issues are addressed by a traditional vision-based smart sorting machine that

separates the workpieces depending on size. The procedure will be carried out using a

single-board minicomputer known as the Raspberry Pi. In the proposed system, Raspberry Pi

camera is used to capture the image/stream video of the incoming workpieces/packages through

the conveyor.

**Materials & Methods**

1. **Camera**: Camera can be of any type internal or external as we are solving the

problem with computer vision. The camera shall be calibrated before working on

the detection algorithm. The main reason for calibrating the camera is because

each camera has two sets of parameters known as intrinsic and extrinsic

parameters. So with the help of these parameters we can actually estimate the

length of the object irrespective of the height of the viewing point from the object.

The code snippet and procedure for calculating the parameters of the camera are

being attached to the source code.

2. **Python3**: We used python3 for coding the project as it is a human readable

language compared to other languages like C++ or C. OpenCv the computer

vision library has a python wrapper which has a huge community for support and

latest updates. Python also helps in quick prototyping compared to other

languages and requires less setup. The version used for this project is 3.10.8

3. **OpenCv**: OpenCV (Open Source Computer Vision Library) is an open source

computer vision and machine learning software library. OpenCV was built to

provide a common infrastructure for computer vision applications and to

accelerate the use of machine perception in the commercial products. Being an

Apache 2 licensed product, OpenCV makes it easy for businesses to utilize and

modify the code. The library has more than 2500 optimized algorithms, which

includes a comprehensive set of both classic and state-of-the-art computer vision

and machine learning algorithms. These algorithms can be used to detect and

recognize faces, identify objects, classify human actions in videos, track camera

movements, track moving objects, extract 3D models of objects, produce 3D point

clouds from stereo cameras, stitch images together to produce a high resolution

image of an entire scene, find similar images from an image database, remove red

eyes from images taken using flash, follow eye movements, recognize scenery

and establish markers to overlay it with augmented reality, etc. OpenCV has more

than 47 thousand users.

4. **Aruco Tag**:An ArUco marker is a synthetic square marker composed by a wide

black border and an inner binary matrix which determines its identifier (id). The black

border facilitates its fast detection in the image and the binary codification allows its

identification and the application of error detection and correction techniques. The

marker size determines the size of the internal matrix. For instance a marker size of

4x4 is composed of 16 bits.

Some examples of ArUco markers:Some examples of ArUco markers:

It must be noted that a marker can be found rotated in the environment, however, the

detection process needs to be able to determine its original rotation, so that each

corner is identified unequivocally. This is also done based on the binary codification.


**Implementation:**

There are three steps in getting the whole product to work.

1. Generating Aruco Marker : There are several implementations of generating aruco

markers. There are few well known online generators but we have used the

opencv drawmarker library to generate the marker from the dictionary. For the

project we have used 5X5_100 Aruco Tag when printed it measured a size of

11cm X 11cm.

2. Object Detection: We used classical computer vision instead of deep learning or

Machine learning to port the program into edge devices like ESP32 and detect the

objects. Steps followed for object detection are converting the object to a

grayscale and then performing adaptive threshold to find the features of the image

or frame. Then we find the edges of the object and find the contours which help in

detecting the shape and presence of the object.

3. Aruco Tag and Object measurement: Final code integrates all the designed

features into a one single output. We detect the aruco markers and do object

detection for the other objects placed in the view. Considering the aruco tag as a

known object we can perform the pixel to metric conversion. Once we perform

the conversion we compare the size of the object and if the object size is less than

10cm we sort it as a small package and send it to the right bin or else it's

considered as a large package and will be sent to the left bin.


References:
1. https://opencv.org
2. https://pysource.com

