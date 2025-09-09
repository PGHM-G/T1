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



---

## ⚙️ 실행 방법

### 1) 서버 실행
```bash
cmake -B build -S .
cmake --build build --config Release
./build/bin/Release/GameServer.exe

