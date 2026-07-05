# Java Web Application Server 학습

『자바 웹 프로그래밍 Next Step』 3~6장의 웹 애플리케이션 서버 실습 프로젝트다.

원본 프로젝트와 달리 다음 환경을 사용한다.

- Java 21
- Maven 대신 Gradle 9.6.1
- Windows 로컬 개발 환경
- Git Bash를 이용한 Linux 형식 명령어
- AWS EC2 Linux 인스턴스 배포

## 원격 저장소

- `origin`: `https://github.com/liarreez/web-application-server.git`
- `upstream`: `https://github.com/slipp/web-application-server.git`

원본 저장소의 최신 변경을 가져올 때는 다음 명령을 사용한다.

```bash
git fetch upstream
git switch master
git merge upstream/master
```

## Gradle Wrapper

이 프로젝트는 Gradle Wrapper를 사용하므로 Gradle을 별도로 설치할 필요가 없다.
Wrapper가 프로젝트에서 지정한 Gradle 버전을 내려받아 모든 환경에서 같은 버전으로 빌드한다.

Windows PowerShell:

```powershell
.\gradlew.bat test
```

Git Bash, Linux, macOS:

```bash
./gradlew test
```

## 웹 서버 실행

Windows PowerShell:

```powershell
.\gradlew.bat run
```

Git Bash, Linux, macOS:

```bash
./gradlew run
```

다른 터미널에서 응답을 확인한다.

```bash
curl http://localhost:8080
```

정상 응답:

```text
Hello World
```

서버는 `Ctrl+C`로 종료한다.

## 배포본 만들기

```bash
./gradlew clean test installDist
```

생성 위치:

```text
build/install/web-application-server
```

배포본에는 실행 스크립트, 애플리케이션 JAR, 의존 라이브러리와 `webapp` 정적 파일이 포함된다.
