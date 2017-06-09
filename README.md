# fuzzer-android

1.clone code
```
$ git clone https://github.com/juneJuly/fuzzer-android.git
```
2.download ndk-10e
```
$ wget https://dl.google.com/android/repository/android-ndk-r10e-linux-x86_64.zip?hl=zh-cn
$ unzip android-ndk-r10e-linux-x86_64.zip
```

3.make
```
$ cd ./fuzzer-android/trinity-android/jni
$ ~/android-ndk-r10e/ndk-build
```
4.push libs/armeabi/trinity to device
```
$ adb push libs/armeabi/trinity /data/local/tmp/
```

5.let's rock
  ```
  # ./trinity --dangerous --random 50 -V /dev/ 2>&1 | tee trinity-fuzz-1.log
  ```
6.Examples:
```
  ./trinity -c splice
  Stress test the splice syscall

  ./trinity -x splice
  Call every syscall except for splice.

  ./trinity -qq -l off -C16
  Turn off logging, and suppress most output to run as fast as possible. Use 16 child processes
```
