# protobuf-2.x.x-android


Compile Android version protobuf in linux environment

tis:To compile the 2.x.x version, you only need to copy the entire directory of google/protobuf to jni/src

```
cd protobuf-2.x.x-android
./build.sh 
```

or

```
cd protobuf-2.x.x-android
ndk-build -j8
```

To compile other versions, you only need to copy the entire google/protobuf directory to the src/main/jni directory

issue:undefined reference to typeinfo for google::protobuf::Message you need to turn on RTTI support. https://developer.android.com/ndk/guides/cpp-support#rtti

To enable RTTI across your whole application in ndk-build, add the following line to your Application.mk file:

APP_CPPFLAGS := -frtti

To enable RTTI for a single ndk-build module, add the following line to the given module in its Android.mk:

LOCAL_CPP_FEATURES := rtti Alternatively, you can use:

LOCAL_CPPFLAGS := -frtti
