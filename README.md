# HUGME Local Docker Environment

HUGME 프로젝트의 로컬 Docker 실행환경을 관리한다.

## Repository 배치

각 Repository는 같은 상위 Directory에 배치한다.

```text
FinalProject
├─ Backend_Hugme
├─ AI_Hugme
└─ Infra_Hugme
```

`Infra_Hugme/docker-compose.yml`은 상대경로를 사용해 Backend와 AI Repository에 접근한다.

```text
../Backend_Hugme
../AI_Hugme
```

## 환경변수

로컬에서 사용하는 환경변수는 각자의 `Infra_Hugme/.env`에서 관리한다.

```text
Infra_Hugme
├─ docker-compose.yml
├─ .env
└─ README.md
```

## 최초 실행

Docker Desktop을 실행한 뒤 `Infra_Hugme` Directory에서 실행한다.

```bash
docker compose up -d --build
```

현재 Docker Compose에서 관리하는 Service는 다음과 같다.

```text
postgres
paradedb
elasticsearch
ai
backend
```

## Container 상태 확인

실행 중인 Container 상태를 확인한다.

```bash
docker compose ps
```

## Log 확인

전체 Service의 Log를 확인한다.

```bash
docker compose logs
```

전체 Log를 실시간으로 확인한다.

```bash
docker compose logs -f
```

Backend Log만 확인한다.

```bash
docker compose logs -f backend
```

AI Log만 확인한다.

```bash
docker compose logs -f ai
```

## Backend 다시 Build하기

Backend Source가 변경된 경우 Backend Image를 다시 Build하고 Container를 실행한다.

```bash
docker compose up -d --build backend
```

## AI 다시 Build하기

AI Source가 변경된 경우 AI Image를 다시 Build하고 Container를 실행한다.

```bash
docker compose up -d --build ai
```

## 전체 Container 중지하기

실행 중인 Container를 중지하고 삭제한다.

```bash
docker compose down
```

Docker Volume의 데이터는 유지된다.

Volume까지 포함하여 로컬 데이터를 모두 삭제해야 하는 경우에만 다음 명령을 사용한다.

```bash
docker compose down -v
```
