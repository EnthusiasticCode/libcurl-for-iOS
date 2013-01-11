* libcurl for iOS

This project is a very raugh compilation of an old relise of [libcurl](http://curl.haxx.se/libcurl/) for iOS. It may one day updated to use the actual [libcurl repository](https://github.com/bagder/curl).

** Build instruction

In the curl directory execute:

```
export CC=/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/usr/bin/arm-apple-darwin10-llvm-gcc-4.2 
export CFLAGS="-isysroot /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS6.0.sdk"
export LDFLAGS="-isysroot /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS6.0.sdk -Wl,-syslibroot /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS6.0.sdk"
export CPP=/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/usr/bin/llvm-cpp-4.2 
./configure --disable-shared --without-ssl --without-libssh2 --without-ca-bundle --without-ldap --disable-ldap --host=arm-apple-darwin10
```

Note that you may need to update the iOS SDK references in those exports.

If your want to build libcurl with SSH support, consider cloning [libssh2-for-iOS](https://github.com/x2on/libssh2-for-iOS) and then configure with:

```
./configure --disable-shared --without-ssl --with-libssh2=../../libssh2-for-iOS/bin/iPhoneOS6.0-armv7s.sdk --without-ca-bundle --without-ldap --disable-ldap --host=arm-apple-darwin10
```

If everything went well, you should now be able to build a static iOS library using the XCode project in this repository.