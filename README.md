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

#### Requirements

- Xcode 9.3

#### Add grpc-swift

```
$ git submodule add git@github.com:KyoheiG3/grpc-swift.git
$ cd grpc-swift
```

## Make Project

#### generate-xcodeproj

```
$ make project
```

#### remove ignore

```
$ vim .gitignore
```

```
#/SwiftGRPC.xcodeproj
```

#### edit modulemaps

```
$ vim SwiftGRPC.xcodeproj/GeneratedModuleMap/BoringSSL/module.modulemap
```

```
umbrella "../../../../grpc-swift/Sources/BoringSSL/include"
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

#### Remove RootsEncoder, Simple, Echo, protoc-gen-swift and protoc-gen-swiftgrpc from TARGET

| before | after |
|---|---|
| <img width="173" alt="2018-04-11 13 24 02" src="https://user-images.githubusercontent.com/5707132/38596383-3451ee50-3d8c-11e8-8142-094aa4a83094.png"> | <img width="172" alt="2018-04-11 13 26 28" src="https://user-images.githubusercontent.com/5707132/38596387-36864d6a-3d8c-11e8-9141-e5846068e755.png"> |

## MyProject Build Settings

#### Add SwiftGRPC Project

<img width="272" alt="2017-10-27 11 49 33" src="https://user-images.githubusercontent.com/5707132/32085944-faadaa42-bb0c-11e7-9e82-b80cb23051f4.png">

#### Embed Binary

<img width="870" alt="2018-04-11 13 48 50" src="https://user-images.githubusercontent.com/5707132/38596880-2b9ed14e-3d8f-11e8-9c57-e2efa9ccc419.png">

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
