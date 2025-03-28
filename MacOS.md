# MacOS上的安装教程
## 下载解压opencv源码
```
curl -L -o opencv-4.11.0.tar.gz https://github.com/opencv/opencv/archive/refs/tags/4.11.0.tar.gz
curl -L -o opencv_contrib-4.11.0.tar.gz https://github.com/opencv/opencv_contrib/archive/refs/tags/4.11.0.tar.gz
tar -zxf opencv-4.11.0.tar.gz
tar -zxf opencv_contrib-4.11.0.tar.gz
```
## 生成Debug版本
```
mkdir -p opencv-4.11.0/build_debug
cd opencv-4.11.0/build_debug
cmake .. \
    -G "Ninja" \
    -DCMAKE_BUILD_TYPE=Debug \
    -DCMAKE_INSTALL_PREFIX=/usr/local/opencv_debug/ \
    -DOPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-4.11.0/modules \
    -DOPENCV_ENABLE_NONFREE=ON \
    -DBUILD_PERF_TESTS=OFF -DBUILD_TESTS=OFF \
    -DBUILD_opencv_face=OFF -DBUILD_opencv_wechat_qrcode=OFF -DBUILD_opencv_features2d=OFF -DBUILD_opencv_xfeatures2d=OFF \
    -DENABLE_FAST_MATH=ON \
    -DOPENCV_DNN_OPENCL=ON \
    -DENABLE_NEON=ON -DCPU_BASELINE=NEON -DCPU_DISPATCH=NEON_FP16 \
ninja
mkdir -p /usr/local/opencv_debug
sudo ninja install
```
## 生成Release版本
```
mkdir -p opencv-4.11.0/build_release
cd opencv-4.11.0/build_release
cmake .. \
    -G "Ninja" \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr/local/opencv_release/ \
    -DOPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-4.11.0/modules \
    -DOPENCV_ENABLE_NONFREE=ON \
    -DBUILD_PERF_TESTS=OFF -DBUILD_TESTS=OFF \
    -DBUILD_opencv_face=OFF -DBUILD_opencv_wechat_qrcode=OFF -DBUILD_opencv_features2d=OFF -DBUILD_opencv_xfeatures2d=OFF \
    -DENABLE_FAST_MATH=ON \
    -DOPENCV_DNN_OPENCL=ON \
    -DENABLE_NEON=ON -DCPU_BASELINE=NEON -DCPU_DISPATCH=NEON_FP16 \
ninja
mkdir -p /usr/local/opencv_release
sudo ninja install
```
## 验证
```
ls -lh /usr/local/opencv_debug/lib/libopencv_core.4.11.0.dylib
ls -lh /usr/local/opencv_release/lib/libopencv_core.4.11.0.dylib
```
