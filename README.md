# 🎮 Game Server Portfolio (C++ / IOCP / UE5)

이 프로젝트는 **C++ 기반 IOCP 네트워크 서버**와 **Unreal Engine 클라이언트**를 연동한 개인 포트폴리오입니다.  
대규모 동시 접속 환경에서도 안정적으로 동작할 수 있는 서버 구조를 직접 학습하고, 클라이언트와의 연동 과정에서 발생한 문제를 해결하며 역량을 키웠습니다.

---

## ✨ 주요 특징

- **IOCP 기반 이벤트 루프**  
  Windows IOCP(Completion Port)를 활용해 수천 개의 연결을 효율적으로 처리

- **JobQueue & GlobalQueue**  
  객체 단위 JobQueue로 스레드 안전성 확보, GlobalQueue로 부하 분산 처리

- **멀티스레드 동시성 제어**  
  CoreTLS(Thread Local Storage), DeadLockProfiler를 통한 안정적 스레드 관리

- **메모리 관리**  
  MemoryPool, ObjectPool, Allocator 설계로 효율적인 메모리 사용

- **Protobuf 직렬화**  
  Google Protobuf를 활용한 패킷 정의 및 자동화 툴 제작

- **클라이언트 연동**  
  Unreal Engine 5 기반 클라이언트와 통신, AOI 기반 스폰/디스폰 기능 구현

- **문제 해결 경험**  
  - AOI 재스폰 버그 해결 (클라 Players 맵 제거 누락 수정)  
  - Debug/Release 빌드 불일치 문제 분석 및 대응

---

## 🖼️ 데모

| AOI Despawn | AOI Respawn |
|-------------|-------------|
| ![despawn](docs/images/despawn.gif) | ![respawn](docs/images/respawn.gif) |

- 🔗 [시연 영상(YouTube)](https://youtu.be/demo-link)  

---

## 🏗️ 프로젝트 구조
GameServerPortfolio/

├── ServerCore/ # IOCP, JobQueue, MemoryPool 등 서버 코어

├── GameServer/ # 게임 서버 (Room, Player, AOI, PacketHandler)

├── Client (Unreal Project)/ # UE5 클라이언트

├── ProtobufCore/ # 패킷 정의 및 자동화 툴

└── README.md


---

## ⚙️ 실행 방법

### 1) 서버 실행
```bash
cmake -B build -S .
cmake --build build --config Release
./build/bin/Release/GameServer.exe
```
현재 Debug 모드에서는 라이브러리 불일치 문제로 실행이 되지 않고, Release 모드에서 안정적으로 실행 가능합니다.

---

## 📚 기술 스택

- 언어: C++17

- 네트워크: Windows IOCP

- 직렬화: Google Protobuf

- 클라이언트: Unreal Engine 5.3

- 빌드/의존성 관리: CMake, vcpkg

- 버전 관리: Git, GitHub

---

## 🛠️ 문제 해결 사례
1. AOI 재스폰 버그

- 문제: 플레이어가 멀어지면 캐릭터가 사라지지만, 다시 접근해도 스폰되지 않음

- 원인: 클라이언트의 Players 맵에서 삭제 로직 누락

- 해결: HandleDespawn에서 Players.Remove 추가 → 정상적으로 재스폰 확인

2. Debug/Release 실행 불일치

- 문제: Debug 모드 실행 불가, Release 모드만 가능

- 원인 추정: 라이브러리/런타임 불일치 (Protobuf, vcpkg)

- 배운 점: C++ 빌드 환경과 런타임 의존성 관리의 중요성

---

## 📝 배운 점

서버 구조를 단순히 사용하는 것이 아니라, 왜 이런 설계가 필요한지 깊이 이해할 수 있었습니다.

문제를 단순히 우회하는 대신, 근본 원인을 찾아 해결하는 과정에서 자신감을 얻었습니다.

게임 서버 개발은 끊임없는 디버깅과 안정성 확보의 연속이라는 사실을 체감했습니다.



