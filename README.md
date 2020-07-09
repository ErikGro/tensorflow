# Fork of offical Tensorflow repository with support for building tensorflow lite for roboVM-iOS

## Prerequisites
- macOS
- bazel (brew install bazel)
- numpy (pip3 install numpy)

## Building tensorflow lite for RoboVM iOS Project
Since we need tensorflow lite with java-API we can use the same rule, which is used for building tensorflow lite for android.
Execute follwing command from repository root directory to create library for device:
```bash
bazel build --config=ios_arm64 tensorflow/lite/java:tensorflowlitelib
```
and for simulator:
```bash
bazel build --config=x_86_64 tensorflow/lite/java:tensorflowlitelib
```
Both command create ```libtensorflowlite_jni.so```  in ```bazel-bin/tensorflow/lite/java/```

If you want to create a fat binary which contains both libraries for ```x_86_64``` and ```arm64``` you have to save the first created library and then glue them together via lipo command.
