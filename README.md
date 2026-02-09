# advanced-kindmap-system

1인 풀스택 지하철 경로 안내 시스템을 위한 모노레포입니다.  
지하철 노선 데이터, 최단 경로 탐색 엔진, 백엔드 API, 프론트엔드 웹 클라이언트를 한 저장소에서 통합 관리합니다.

## 모노레포 구조

- `services/backend`  
  - Spring Boot 기반 백엔드 서비스 (REST API, 인증, 요금/환승 로직 등 구현 예정)

- `services/frontend`  
  - React + Vite 기반 웹 프론트엔드 (노선도 시각화, 경로 검색 UI 등 구현 예정)

- `services/cpp-route-engine`  
  - C++로 작성된 고성능 경로 탐색 엔진 (최단 경로, 환승 최소화, 시간 가중치 등 알고리즘 구현 예정)

- `database/migrations`  
  - DB 마이그레이션 스크립트 및 스키마 정의 관리 디렉토리

- `infrastructure/docker`  
  - Dockerfile, docker-compose, 인프라 관련 스크립트/설정 파일

- `shared/api-contracts`  
  - 백엔드와 프론트엔드 간에 공유되는 API 스키마, DTO, 타입 정의 등

## 패키지 관리

루트의 `package.json`은 다음과 같이 워크스페이스를 정의합니다.

- `services/*`
- `shared/*`

Java(Sprint Boot)와 C++ 서비스는 빌드 도구(Gradle, Maven, CMake 등)를 각 디렉토리별로 추가해 사용할 수 있고,  
Node 기반 프로젝트(프론트엔드, 공유 라이브러리 등)는 워크스페이스를 통해 의존성을 일관되게 관리합니다.

## 초기 세팅

```bash
# (이미 실행되었다면 생략 가능)
bash init_project.sh
```

이 스크립트는 위에서 설명한 디렉토리 구조와 기본 설정 파일(`package.json`, `.gitignore`, `README.md`)을 생성합니다.

## 다음 단계 제안

1. `services/backend`에 Spring Boot 프로젝트 초기화 (Gradle 또는 Maven 사용)  
2. `services/frontend`에 React + Vite 템플릿 생성  
3. `services/cpp-route-engine`에 CMake 기반 C++ 프로젝트 구성  
4. `database/migrations`에 초기 스키마 및 예시 데이터 마이그레이션 추가  
5. `infrastructure/docker`에 각 서비스용 Dockerfile 및 통합 `docker-compose.yml` 구성  

