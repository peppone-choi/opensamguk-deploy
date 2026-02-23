# OpenSamguk Deploy

오픈삼국 배포 전용 저장소입니다.
애플리케이션 소스 코드는 포함하지 않고, 운영에 필요한 배포 파일만 관리합니다.

## 포함 파일

- `docker-compose.yml`
- `nginx/nginx.conf`
- `.env.example`

## 빠른 시작

1) 환경변수 파일 생성

```bash
cp .env.example .env
```

2) `.env` 값 수정 (최소 `DB_PASSWORD`는 반드시 변경)

3) 이미지 pull 및 컨테이너 기동

```bash
docker compose pull
docker compose up -d
```

## 업데이트

최신 이미지로 갱신:

```bash
docker compose pull
docker compose up -d
```

특정 버전(커밋 SHA) 고정 배포:

```bash
TAG=<commit-sha> docker compose up -d
```

## 구성 개요

- `postgres`: PostgreSQL 16
- `redis`: Redis 7
- `gateway`: `ghcr.io/peppone-choi/opensam-gateway`
- `frontend`: `ghcr.io/peppone-choi/opensam-frontend`
- `nginx`: 외부 진입점(reverse proxy)

`game-app` 버전 컨테이너는 `gateway`가 Docker socket을 통해 동적으로 관리합니다.
