# gRPCExample

This is example to use with gRPC Swift for iOS.

1. Update submodules

```
$ git submodule update --init
```

2. Build packages

```
$ cd grpc-swift
$ make
```

# How to build grpc-swift

#### Add grpc-swift

```
$ git submodule add git@github.com:KyoheiG3/grpc-swift.git
$ cd grpc-swift
```

## Make Project

#### generate-xcodeproj

```
$ make
$ vim Makefile
```

```
#swift package generate-xcodeproj
```

#### remove ignore

```
$ vim .gitignore
```

```
#SwiftGRPC.xcodeproj
```

#### edit modulemaps

```
$ vim SwiftGRPC.xcodeproj/GeneratedModuleMap/BoringSSL/module.modulemap
```

```
umbrella "../../../../grpc-swift/Sources/BoringSSL/include"
```

```
$ vim SwiftGRPC.xcodeproj/GeneratedModuleMap/Czlib/module.modulemap
```

```
umbrella "../../../../grpc-swift/.build/checkouts/zlib.git--9016602441419864029/Sources/Czlib/include"
```

This is not required. However, if you don't change, others may get build error.

## SwiftGRPC Build Settings

```
$ open ./SwiftGRPC.xcodeproj
```

#### Change Base SDK

```
SDKROOT = iphoneos
```

<img width="870" alt="2017-10-27 10 11 42" src="https://user-images.githubusercontent.com/5707132/32085117-45b18e28-bb08-11e7-9fda-36bc4dcc519e.png">

#### Change Supported Platforms

```
SUPPORTED_PLATFORMS = "iphonesimulator iphoneos"
```

<img width="870" alt="2017-10-27 10 11 57" src="https://user-images.githubusercontent.com/5707132/32085125-523d839a-bb08-11e7-99bd-cb43ea9f13f9.png">

#### Change Deployment Target

```
IPHONEOS_DEPLOYMENT_TARGET = 9.0
```

<img width="870" alt="2017-10-27 10 12 37" src="https://user-images.githubusercontent.com/5707132/32085142-64ad3912-bb08-11e7-84b2-c06cbfb0a7c5.png">

#### Change Swift Language Version

```
SWIFT_VERSION = 4.0
```

<img width="870" alt="2017-10-27 10 13 50" src="https://user-images.githubusercontent.com/5707132/32085149-6961f812-bb08-11e7-91a6-8b47d3b78b46.png">

#### Remove zlib-example from TARGET

<img width="165" alt="2017-10-27 10 22 54" src="https://user-images.githubusercontent.com/5707132/32085181-7fe3c836-bb08-11e7-9960-f76e83627c29.png">

## MyProject Build Settings

#### Add SwiftGRPC Project

<img width="272" alt="2017-10-27 11 49 33" src="https://user-images.githubusercontent.com/5707132/32085944-faadaa42-bb0c-11e7-9e82-b80cb23051f4.png">

#### Link Binary With Libraries

<img width="1129" alt="2017-10-27 10 27 05" src="https://user-images.githubusercontent.com/5707132/32085184-85fde0ee-bb08-11e7-89a8-8fe18d3d7365.png">

#### Copy Files

<img width="1129" alt="2017-10-27 10 27 19" src="https://user-images.githubusercontent.com/5707132/32085187-9043bd4e-bb08-11e7-9cae-654580df0c2d.png">

#### Add Header Search Paths

```
HEADER_SEARCH_PATHS = $(SRCROOT)/grpc-swift/Sources/CgRPC/include
```

<img width="1129" alt="2017-10-27 10 30 37" src="https://user-images.githubusercontent.com/5707132/32085212-a6ca0d98-bb08-11e7-8c51-9142d93e3285.png">

#### Disable Bitcode

```
ENABLE_BITCODE = NO
```

If you don't change, Cannot export ipa.

<img width="1130" alt="2017-10-27 10 27 59" src="https://user-images.githubusercontent.com/5707132/32085190-955592a8-bb08-11e7-9a82-19a72994a39a.png">

#### Add Configurations

If your project is added some configurations, `SwiftGRPC` also should be added same configurations.

##### MyProject

<img width="1129" alt="2017-10-27 10 34 50" src="https://user-images.githubusercontent.com/5707132/32085224-b1f7728c-bb08-11e7-8157-2bfa83b99b3d.png">

##### SwiftGRPC

<img width="1129" alt="2017-10-27 10 34 24" src="https://user-images.githubusercontent.com/5707132/32085219-acd5e040-bb08-11e7-8344-f61ead711022.png">
