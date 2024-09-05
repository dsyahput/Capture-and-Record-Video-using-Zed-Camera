# Capture and Record Video using Zed Camera

## A. Prerequisites:

  1. Install ZED SDK:
      Download and install the ZED SDK from Stereolabs ZED SDK website.
  2. Install OpenCV:
      Make sure OpenCV is installed. If not, you can follow OpenCV installation instructions for your platform.
## B. Build the Program
Create a build directory: Open a terminal and navigate to the directory containing the program and the CMakeLists.txt file, then create a build directory:

``` bash
cd Capture-and-Record-Video-using-Zed-Camera
mkdir build
cd build
cmake ..
make
```
## C. Run the Program
After building the program, you can run it with the following command:
```bash
./zed_camera_record
```

Press the 's' key to start recording the video.  
Press the 'x' key to stop the recording.  
Press 'Esc' to exit the program.  
### The video will be saved in the 'videos' folder.
