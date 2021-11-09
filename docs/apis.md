# Hcloner API 문서
Hcloner 사용자 정의 스크립트의 API문서입니다.
## Api
시스템, Script의 정보를 얻어오는데 사용합니다.
### 운영체제
```
String getOS()
```
운영체제의 종류를 반환합니다.
```
boolean isMacOSX()
```
Mac OS 계열 운영체제인 경우 true, 아니면 false를 반환합니다.
```
boolean isUnix()
```
Unix 계열 운영체제인 경우 true, 아니면 false를 반환합니다.
```
boolean isWindows()
```
Windows 운영체제인 경우 true, 아니면 false를 반환합니다.
### CPU
```
boolean is64Bit()
```
CPU가 64비트로 동작중이면 true, 아니면 false를 반환합니다.
```
int getAvailableProcessors()
```
활성화되어있는 CPU코어의 갯수를 반환합니다.

int를 반환한다 써져있으나 실제로는 long을 반환합니다.(int로 고칠 예정)
### 메모리
JVM에서 사용가능한 힙을 기준으로 작동합니다.
```
long getFreeMemory()
```
사용가능한 빈 메모리의 크기를 반환합니다.
```
long getMaxMemory()
```
사용가능한 최대 메모리의 크기를 반환합니다.
```
long getTotalMemory()
```
사용중인 총 메모리의 크기를 반환합니다.
### 스크립트
스크립트의 이름은 스크립트의 경로와 동일합니다.
```
String[] getScripts()
```
전체 스크립트의 목록을 반환합니다.
```
String getScript()
```
현재 스크립트의 이름을 반환합니다.
## App
```
String getNewPackageName()
```
바뀐 패키지 명을 반환합니다.
```
String getNewApkPath()
```
패키지명을 바꾸고 저장할 위치를 반환합니다.
```
String getOriginalPackageName()
```
원본 패키지명을 반환합니다.
```
String getOriginalApkPath()
```
원본 APK의 위치를 반환합니다.
## Cloner
```
String getVersion()
```
Hcloner의 버전을 반환합니다.
```
String getDeployType()
```
Hcloner의 배포상태를 반환합니다. 대부분의 경우 RELEASE입니다.
```
getApktoolVersion()
```
Hcloner가 사용하는 Apktool의 버전을 반환합니다.
```
String getTemp()
```
임시폴더의 경로를 반환합니다.

임시폴더에는 디컴파일된 APK의 바이트코드가 있습니다.
## FileStream
```
String read(String path)
```
path에 있는 파일의 내용을 `String`으로 반환합니다.
```
byte[] readAsByte(String path)
```
path에 있는 파일의 내용을 `byte[]`로 반환합니다.
```
boolean write(String path, String content)
```
```
boolean writeAsByte(String path, byte[] content)
```
path에 content를 씁니다. 성공하면 true, 실패하면 false를 반환합니다.
```
boolean move(String from, String to)
```
from에 있는 파일을 to로 옮깁니다. 성공하면 true, 실패하면 false를 반환합니다.
```
boolean copy(String from, String to)
```
from에 있는 파일을 to로 복사합니다. 성공하면 true, 실패하면 false를 반환합니다.
```
boolean exists(String path)
```
path에 파일또는 폴더가 있으면 true, 없으면 false를 반환합니다.
```
boolean isFile(String path)
```
path가 파일이면 true, 아니면 false를 반환합니다.
```
boolean isDirectory(String path)
```
path가 폴더이면 true, 아니면 false를 반환합니다.

```
String[] files(String path)
```
path에 있는 하위 파일과 폴더들의 경로를 `String[]`으로 반환합니다.
## Log
`스크립트 이름-[로그 태그]: 로그 내용`과 같이 콘솔에 출력합니다.
```
void error(String message)
```
```
void e(String message)
```
`Err` 태크로 message를 출력합니다
```
void warning(String message)
```
```
void w(String message)
```
`Warn` 태크로 message를 출력합니다
```
void info(String message)
```
```
void i(String message)
```
`Info` 태크로 message를 출력합니다
```
void debug(String message)
```
```
void d(String message)
```
`DBG` 태크로 message를 출력합니다
## SharedData
스크립트끼리 공유하는 `키-값` 쌍으로 저장되는 데이터입니다.
```
String[] getKeys()
```
key의 목록을 `String[]`으로 반환합니다.
```
void put(String key, Object value)
```
`key`를 키, `value`를 값으로 하여 데이터를 저장합니다.
```
Object get(String key)
```
`key`를 키로 하여 값을 얻습니다.
```
int size()
```
저장된 쌍의 갯수를 반환합니다.
```
boolean empty()
```
비어있다면 true, 아니면 false를 반환합니다.
