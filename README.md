# Setting Up ESP32-Cam
This only works for the ESP32-Cam-MB, not the ESP32-Cam itself. The difference is that the ESP32-Cam-MB has a second layer & Micro-b port, as shown below.
![ESP32-Cam-MB](https://i2.wp.com/randomnerdtutorials.com/wp-content/uploads/2021/01/ESP32-CAM-MB-Micro-USB-Programmer-CH340G-Serial-Chip.jpg?resize=828,466&quality=100&strip=all&ssl=1)

Follow this tutorial to use the ESP32-cam-webserver library: [Link](https://www.rogerfrost.com/use-a-github-library-and-arduino-ide-to-create-an-esp32-camera-web-server/)
- The above uses this github library for Arduino: [github](https://github.com/easytarget/esp32-cam-webserver)
- Do not uncomment `// #define URL_HOSTNAME "esp-cam"` or `// #define WIFI_AP_ENABLE`
- If done correctly, navigating to http://192.168.1.168:81/view should open the camera view. Double-click to enter fullscreen mode.
# Converting ESP32-Cam output to Webcam
The ESP32-Cam is an IP camera, and the code I used to detect ArUco markers requires a webcam output. To solve this I use OBS Studio & Virtual Cam to stream the ESP32-Cam's browser output as a virtual webcam. 
- Install OBS Studio here: [Link](https://obsproject.com/download)
- Install OBS Virtual Cam here: [Link](https://github.com/CatxFish/obs-virtual-cam/releases)
# Install Code
1. Install the code: `git clone https://github.com/danielchandg/aruco-markers.git`
2. Run `opencv_generate_aruco/opencv_generate_aruco.py` and follow the example usage at the top to generate ArUco markers
- Note that ArUco marker detection works best when ArUco markers have a wide white border on all 4 sides. 
3. Run `opencv-detect-aruco/detect_aruco_image.py` and follow the example usage at the top to detect ArUco markers in an image
4. Run `opencv-detect-aruco/detect_aruco_video.py` to detect ArUco markers using webcam output, or `opencv-detect-aruco/detect_aruco_video_guess_type.py` to detect any ArUco markers and print the ArUco dictionary. 
- Examples from `detect_aruco_video.py`:
![Frame 1](https://i.imgur.com/KeQDS6R.png)
![Frame 2](https://i.imgur.com/Uqg97Kl.png)
![Frame 3](https://i.imgur.com/KccRH8Z.png)