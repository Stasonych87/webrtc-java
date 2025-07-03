[![Build Status](https://img.shields.io/github/actions/workflow/status/devopvoid/webrtc-java/build.yml?label=Build&logo=github)](https://github.com/devopvoid/webrtc-java/actions)
[![Maven Central](https://img.shields.io/maven-central/v/dev.onvoid.webrtc/webrtc-java?label=Maven%20Central&logo=apache-maven)](https://search.maven.org/artifact/dev.onvoid.webrtc/webrtc-java)

## webrtc-java

Реализация собственного интерфейса Java, основанная на бесплатном, открытом [WebRTC](https://webrtc.org ) проект. Цель этого проекта - обеспечить разработку приложений RTC для настольных платформ, работающих под управлением Java. Этот проект обертывает [WebRTC Native API](https://webrtc.github.io/webrtc-org/native-code/native-apis ) и похож на [JS API](https://w3c.github.io/webrtc-pc ).

<!--
### Maven

```xml
<dependency>
	<groupId>dev.onvoid.webrtc</groupId>
	<artifactId>webrtc-java</artifactId>
	<version>0.11.0</version>
</dependency>
```

### Gradle

```groovy
implementation "dev.onvoid.webrtc:webrtc-java:0.10.0"
implementation group: "dev.onvoid.webrtc", name: "webrtc-java", version: "0.10.0", classifier: "windows-x86_64"
implementation group: "dev.onvoid.webrtc", name: "webrtc-java", version: "0.10.0", classifier: "macos-x86_64"
implementation group: "dev.onvoid.webrtc", name: "webrtc-java", version: "0.10.0", classifier: "macos-aarch64"
implementation group: "dev.onvoid.webrtc", name: "webrtc-java", version: "0.10.0", classifier: "linux-x86_64"
implementation group: "dev.onvoid.webrtc", name: "webrtc-java", version: "0.10.0", classifier: "linux-aarch64"
implementation group: "dev.onvoid.webrtc", name: "webrtc-java", version: "0.10.0", classifier: "linux-aarch32"
```
-->


### Подерживаемые платформы
Maven Central artifacts contain native libraries that can be loaded on the following platforms:

<table>
  <tr>
    <td></td>
    <td>x64</td>
    <td>arm</td>
    <td>arm64</td>
  </tr>
  <tr align="center">
    <th>Linux</th>
    <td>✔</td>
    <td>✔ armeabi-v7a</td>
    <td>✔ arm64-v8a</td>
  </tr>
  <tr align="center">
    <th>macOS</th>
    <td>✔</td>
    <td>-</td>
    <td>✔</td>
  </tr>
  <tr align="center">
    <th>Windows</th>
    <td>✔</td>
    <td>-</td>
    <td>-</td>
  </tr>
</table>

Нативные библиотеки созданы с использованием ветки WebRTC M137/6998.

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
| webrtc.branch      | Чекаут ветки WebRTC, которую будем собирать.                                                                                                                               | branch-heads/5615           |
| webrtc.src.dir     | Абсолютный путь к каталогу в который будет выгружено дерево исходников WebRTC.                                                                                             | /\<user_home\>/webrtc       |
| webrtc.install.dir | Путь установки для скомпилированной библиотеки WebRTC. Также используется для привязки к предварительно скомпилированной библиотеке WebRTC для сокращения времени сборки.  | /\<user_home\>/webrtc/build |

Можно так использовать при запуске mvn
```
mvn install "-Dwebrtc.src.dir=D:/testDir/webrtc" "-Dwebrtc.install.dir=D:/testDir/webrtc/build"
```