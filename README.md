# Labs for Computer Vision

## Building opencv from source

1. Install prerequisites. If `libvtk` can't be installed, install it manually.
        
           sudo apt-get install cmake build-essential git unzip python3 libjpeg-dev libpng-dev  \
              python3-pip wget libtbb2 libtbb-dev libtiff-dev libqt5opengl5-dev libqt5gui5 libqwt-qt5-dev  \
              libqt5test5 libqt5concurrent5 libopenblas-dev liblapack-dev  \
              liblapacke-dev libeigen3-dev libavfilter-dev libwebp-dev libopenexr-dev libgdal-dev  \
              libavutil-dev libavcodec-dev libavformat-dev libswscale-dev libavresample-dev libavdevice-dev  \
              libatlas-base-dev libvtk7-dev libv4l-dev libeigen3-dev libatlas-base-dev libatlas-cpp-0.6-dev  \
              libgstreamer1.0-dev gstreamer1.0-plugins-{base,good,bad,ugly}

2. Clone or download both the opencv and opencv-contrib repos and extract them.

3. Create a `build` folder inside the extracted folder.

4. Run this. Check output general config for python 3 settings to ensure cmake detects python. Example pyenv interpreter path: /home/$USER/.pyenv/versions/3.8.5/bin/python.
 
        cmake -Wno-dev     -DCMAKE_BUILD_TYPE=RELEASE     -DOPENCV_EXTRA_MODULES_PATH=path/to/contrib/folder/modules  \
           -DCMAKE_INSTALL_PREFIX=/usr/local/opencv-4.5.2     -DBUILD_opencv_java=OFF -DWITH_OPENGL=ON     -DWITH_OPENCL=ON -DWITH_IPP=OFF -DFORCE_VTK=ON  \
           -DWITH_GDAL=ON -DWITH_XINE=ON     -DENABLE_PRECOMPILED_HEADERS=OFF     -DENABLE_AVX=ON -DWITH_TBB=ON -DWITH_EIGEN=ON     -DWITH_V4L=ON -DWITH_LAPACK=ON -DWITH_QT=ON  \
           -DWITH_FFMPEG=ON -DBUILD_TESTS=OFF     -DBUILD_PERF_TESTS=OFF -DOPENCV_ENABLE_NONFREE=ON \
           -DPYTHON_DEFAULT_EXECUTABLE=path/to/interpreter -DBUILD_opencv_python3=ON -DBUILD_NEW_PYTHON_SUPPORT=ON \
           -DPYTHON3_EXECUTABLE=path/to/interpreter ..
        
5. cmake might need to be updated if Ubuntu 18.04 since official repo doesnt have latest version. Build from source using this [link](https://askubuntu.com/a/865294/835919). 

6. For python, need to `export PYTHONPATH=/usr/local/opencv-4.5.2/lib/python3.8/site-packages` before running. If using Pycharm, can set in `Settings>Project>Interpreter>cog in upper right>Show all>folder thing in upper right`.