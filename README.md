[![](https://github.com/devopvoid/webrtc-java/workflows/Maven%20CI/badge.svg)](https://github.com/devopvoid/webrtc-java/actions)
[![](https://img.shields.io/maven-central/v/dev.onvoid.webrtc/webrtc-java.svg?label=Maven%20Central&logo=apache-maven)](https://search.maven.org/search?q=g:%22dev.onvoid.webrtc%22%20AND%20a:%22webrtc-java%22)

## webrtc-java

Реализация собственного интерфейса Java, основанная на бесплатном, открытом [WebRTC](https://webrtc.org ) проект. Цель этого проекта - обеспечить разработку приложений RTC для настольных платформ, работающих под управлением Java. Этот проект обертывает [WebRTC Native API](https://webrtc.github.io/webrtc-org/native-code/native-apis ) и похож на [JS API](https://w3c.github.io/webrtc-pc ).

<!--
### Maven

```xml
<dependency>
    <groupId>dev.onvoid.webrtc</groupId>
    <artifactId>webrtc-java</artifactId>
    <version>0.7.0</version>
</dependency>
```

### Gradle

```groovy
implementation "dev.onvoid.webrtc:webrtc-java:0.7.0"
implementation group: "dev.onvoid.webrtc", name: "webrtc-java", version: "0.7.0", classifier: "windows-x86_64"
implementation group: "dev.onvoid.webrtc", name: "webrtc-java", version: "0.7.0", classifier: "macos-x86_64"
implementation group: "dev.onvoid.webrtc", name: "webrtc-java", version: "0.7.0", classifier: "linux-x86_64"
```
-->


### Подерживаемые платформы
Maven Central artifacts contain native libraries that can be loaded on the following platforms:

<table>
  <tr>
    <td>Linux</td>
    <td>x86_64</td>
  </tr>
  <tr>
    <td>macOS</td>
    <td>x86_64</td>
  </tr>
  <tr>
    <td>Windows</td>
    <td>x86_64</td>
  </tr>
</table>

Нативные библиотеки созданы с использованием ветки WebRTC M112/5615.

### Примечание к сборке

Чтобы создать машинный код, обязательно установите необходимое программное обеспечение (см. ссылки)

**Примечание**: Вам не нужно устанавливать инструменты Depot Tools, сценарий сборки сделает это за вас.

<table>
  <tr>
    <td>Linux</td>
    <td><a href="https://webrtc.googlesource.com/src/+/refs/heads/master/docs/native-code/development/prerequisite-sw/index.md#linux-ubuntu_debian">Debian & Ubuntu</a>, <a href="https://chromium.googlesource.com/chromium/src/+/master/docs/linux/build_instructions.md#notes">other distros</a></td>
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

по идее можно так использовать при запуске mvn
```
mvn install "-Dwebrtc.src.dir=D:/testDir/webrtc" "-Dwebrtc.install.dir=D:/testDir/webrtc/build"
```