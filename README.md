# Vehicle detection, tracking, and speed estimation using less calibration.
There are many techniques available on the internet which require two reference objects to calculate the speed of a vehicle using a camera.
**Now I am trying to calculate the speed of a vehicle using a single camera and without any reference object and much calibration.**

### The real-life scenarios that can occur in any real-time on a road.

 - One vehicle can enter the scene and leave.
 - Multiple vehicles can enter the scene and leave. These vehicles can enter at different/same times and can leave at different/same times.
 
 ## What is already available on the internet:
 
 - [https://www.pyimagesearch.com/2019/12/02/opencv-vehicle-detection-tracking-and-speed-estimation/](https://www.pyimagesearch.com/2019/12/02/opencv-vehicle-detection-tracking-and-speed-estimation/) This webpage gives step by step process of Vehicle Detection, Tracking, and Speed Estimation using OpenCV, Raspberry Pi, and Intel Movidius NCS.  
 **Drawbacks:** It uses proper calibration and is hard to setup.
 
 - [https://camlytics.com/calculate-vehicle-speed](https://camlytics.com/calculate-vehicle-speed) They use almost the same technique you are using. In place of two cones, they place two lines.  
**Drawbacks:** They provide paid services.
 - [https://www.geeksforgeeks.org/opencv-python-program-vehicle-detection-video-frame/](https://www.geeksforgeeks.org/opencv-python-program-vehicle-detection-video-frame/) OpenCV Python program for Vehicle detection in a video frame.  
 **Drawbacks:** Too slow to implement in realtime. 

### Some common drawbacks of currently available solutions:

 - Cannot properly detect each vehicle separately in a video.
 - Too slow to implement in realtime. 
 - Not able to measure individual speed of different vehicles at a time in a video.
 
 According to my approach, we can overcome the above-mentioned drawbacks. 

## My approach:
**Things I am assuming:**
 - We have a camera mounted on a tree or a pole that records or captures video in real-time as shown in the demo video.
 - We know the distance in kilometers or meters which the camera captures.
 - We know the framerate at which our camera captures the video.

 1. We will detect and track the vehicle as soon as it enters the scene.
 2. For each vehicle we track, we will assign a unique ID to it. So that we can measure speed for each vehicle detected.
 3. Can detect and track vehicles using some open source libraries like OpenCV or YOLO or can train a custom model.
 4. We can simultaneously use different methods to better detect and track vehicles.
 5. Then we will implement the technique mentioned in this link to calculate speed without much calibration. [https://answers.opencv.org/question/98670/finding-speed-of-vehicle-in-video/](https://answers.opencv.org/question/98670/finding-speed-of-vehicle-in-video/)
 For each vehicle detected, we will do the following:
 - Count the total number of frames in which the vehicle was present. The fast-moving vehicle will be present in less number of frames as compared to slow-moving vehicles.
 - Time [seconds] = Total [Frames] / [Frames / Second] .
 - Distance is already known. (the distance our camera is capturing).
 - Speed = Distance / Time
 6. The computer vision task requires a system with good computation power. And we cannot use such a system at each site where we will implement our solution due to cost factors. But nowadays fast internet is easily available at affordable prices.
 7. So we will Develop Machine Learning and Data Pipelines.
 8. The video feed will be sent to a high computing system and the system will measure the speed for each vehicle in real-time.
 9. Due to Pipelines, maintenance and upgrades will be easier.
 
 This is my approach to the speed estimation of a vehicle. All feedback and suggestions are welcome. Anybody who wants to work on this approach can contact me. 
