# Docker

# What is docker?

도커는 컨테이너 기반의 오픈소스 가상화 플랫폼이다. 다른 도구와 마찬가지로 **어떤 문제**를 해결하기 위해 만들어졌고 그 방법이 많은 사람들에게 인기를 끌면서 널리 사용되고 있다.

그렇다면, **어떤 문제**란 무엇일까?

# Why docker?

## 서버를 관리한다는 것

AWS, Azure, Google Cloude, ... 수 많은 서버환경과 Node.js, Python, Ruby, ... 수 많은 개발환경 처럼 계속해서 변하는 외부 환경이 존재한다. 

# Docker Command

docker run -d -p {port} -e {environment} —name {name} IMAGE[:TAG]

## Exec : enter the docker container

실행 중인 도커 컨테이너에 접속할 때 사용하며, 도커에서는 컨테이너 안에 접속할 때 ssh를 권장하지 않고 exec로 접속할 것을 권장

docker exec —help

# Docker-Compose Command

### dko build

필요한 이미지를 빌드

### dko up

서비스를 구동 (서비스와 네트워크가 없으면 만들고, 이미지가 없으면 빌드)

- —build: 강제로 이미지 재빌드
- —forcs-recreate: 컨테이너 재생성
- -d : 데몬 모드로 실행

### dko ps

현재 실행 중인 서비스 목록 보기

- name : 디렉토리명-서비스명-숫자
- command : 현재 실행되고 있는 명령어
- ports : 호스트와 서비스 간에 네트워크 관계

### dko logs [service]

- -f : 로그 계속 추적
- —tail

### dko top [service]

서비스 내에서 실행 중인 프로세스 목록 보기

### dko stop/start [service]

실행 중인 서비스 중지/시작

### dko exec {container} {command}

현재 dko 파일이 존재하는 서비스의 컨테이너에서 명령어를 실행

- -e : 환경변수를 설정

```
💡 주의!

여기서 모든 docker-compose 명령어들은 현재 디렉토리에 존재하는 docker-compose.yml 파일에 정의된 서비스들에서만 실행되는 것임
즉, 다른 디렉토리로 가면 그 디렉토리에 존재하는 docker-compose 파일을 읽어드리고 실행하게 됨. 이것은 docker-compose ps -a 로 확인 가능
docker ps -a 과 비교해보면 알 수 있을 것
```

### dko run {container} {command}

해당 서비스에 컨테이너를 하나 더 실행

- -d : 데몬 모드로 실행

### dko down [service] = stop + kill

서비스를 멈추고, 컨테이너를 삭제

- -v : 도커 볼륨도 함께 삭제