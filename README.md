[![Build Status](https://img.shields.io/github/actions/workflow/status/devopvoid/webrtc-java/build.yml?label=Build&logo=github)](https://github.com/devopvoid/webrtc-java/actions)
[![Maven Central](https://img.shields.io/maven-central/v/dev.onvoid.webrtc/webrtc-java?label=Maven%20Central&logo=apache-maven)](https://search.maven.org/artifact/dev.onvoid.webrtc/webrtc-java)

<p align="center">
  <img alt="webrtc-java" width="100px" src="https://jrtc.dev/assets/images/logo.png" />
  <h2 align="center">Connecting the Java world through WebRTC</h2>
</p>

webrtc-java is a Java wrapper for the [WebRTC Native API](https://webrtc.github.io/webrtc-org/native-code/native-apis), providing similar functionality to the [W3C JavaScript API](https://w3c.github.io/webrtc-pc). It allows Java developers to build real-time communication applications for desktop platforms without having to work directly with native code.

The library provides a comprehensive set of Java classes that map to the WebRTC C++ API, making it possible to establish peer-to-peer connections, transmit audio and video, share screens, and exchange arbitrary data between applications.

## Features

- **Complete WebRTC API implementation** - Includes peer connections, media devices, data channels, and more
- **Cross-platform support** - Works on Windows, macOS, and Linux (x64, ARM, ARM64)
- **Media capabilities** - Audio and video capture from cameras and microphones
- **Desktop capture** - Screen and application window sharing
- **Data channels** - Bidirectional peer-to-peer data exchange
- **Statistics API** - Detailed metrics for monitoring connection quality
- **Simple integration** - Available as a Maven dependency
- **Native performance** - Thin JNI layer with minimal overhead

## Getting Started

For more detailed information, check out the documentation:

- [Quickstart](https://jrtc.dev/#/quickstart) - Get up and running quickly with webrtc-java
- [Guides](https://jrtc.dev/#/guide/overview) - Comprehensive documentation on using the library
- [Examples](https://jrtc.dev/#/examples) - Sample code demonstrating various features
- [Build Notes](https://jrtc.dev/#/build) - Instructions for building the library from source

### Примечание к сборке

Чтобы создать машинный код, обязательно установите необходимое программное обеспечение (см. ссылки)

**Примечание**: Вам не нужно устанавливать инструменты Depot Tools, сценарий сборки сделает это за вас.
Для Linux (пример Ubuntu) возможно понадобится установить **build-essential** и некоторые доп. либы
```
sudo apt install -y build-essential libpulse-dev libudev-dev xorg-dev pulseaudio libasound2-dev libv4l-dev
```
<table>
  <tr>
    <td>Linux</td>
    <td><a href="https://chromium.googlesource.com/chromium/src/+/master/docs/linux/build_instructions.md#system-requirements">Ubuntu</a>, <a href="https://chromium.googlesource.com/chromium/src/+/master/docs/linux/build_instructions.md#Notes-for-other-distros">other distros</a></td>
  </tr>
  <tr>
    <td>macOS</td>
    <td>Xcode 9 or higher</td>
  </tr>
  <tr>
    <td>Windows</td>
    <td><a href="https://chromium.googlesource.com/chromium/src/+/master/docs/windows_build_instructions.md#visual-studio">Visual Studio</a></td>
  </tr>
</table>

Если у вас установлены все необходимые компоненты для вашей операционной системы, запустите:

```
mvn install
```

При первом запуске, дерево исходников WebRTC будет загружено в каталог, указанный в параметре webrtc.src.dir. По умолчанию параметр имеет значение `/<user home>/webrtc`.
Его можно изменить, если например на диске C мало места, т.к. потребуется примерно 12 Гб свободного места
#### Build Parameters

| Parameter          | Description                                                                                                                                                                | Default Value               |
| ------------------ |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------|
| webrtc.branch      | Чекаут ветки WebRTC, которую будем собирать.                                                                                                                               | branch-heads/7204            |
| webrtc.src.dir     | Абсолютный путь к каталогу в который будет выгружено дерево исходников WebRTC.                                                                                             | /\<user_home\>/webrtc       |
| webrtc.install.dir | Путь установки для скомпилированной библиотеки WebRTC. Также используется для привязки к предварительно скомпилированной библиотеке WebRTC для сокращения времени сборки.  | /\<user_home\>/webrtc/build |

Можно так использовать при запуске mvn
```
mvn install "-Dwebrtc.src.dir=D:/testDir/webrtc" "-Dwebrtc.install.dir=D:/testDir/webrtc/build"
```

## License

Copyright (c) 2019 Alex Andres

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.