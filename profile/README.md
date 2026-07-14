# Pillioo

## Project Overview

Pillioo는 의약품 리콜 및 안전 이벤트 대응을 돕는 약사 중심 의사결정 지원 시스템입니다.

외부 리콜 정보, 내부 재고 데이터, 근거 문서, AI 보고서 초안, 약사 검토, 승인 이력, 감사 로그를 하나의 워크플로우로 연결합니다. 시스템은 최종 판단을 자동으로 내리지 않으며, 약사 또는 권한 있는 담당자의 검토를 전제로 합니다.

이 프로젝트는 리콜 이벤트가 들어온 뒤 내부 재고와 영향을 비교하고, 관련 근거를 검색한 다음, 검토 가능한 보고서 초안을 생성하는 흐름을 구현했습니다.

## Preview


<!-- Product Entrance 화면 캡처 삽입 위치 -->
<!-- Safety Inbox 화면 캡처 삽입 위치 -->
<!-- Ticket Workspace 화면 캡처 삽입 위치 -->
<!-- Pharmacist Review 화면 캡처 삽입 위치 -->
<!-- Evidence 또는 Report 화면 캡처 삽입 위치 -->
<!-- 데모 GIF 또는 영상 삽입 위치 -->

## Demo

<!-- 영상 -->

## Tech Stack

| 영역 | 기술 | 역할 |
|---|---|---|
| Frontend | React, TypeScript, Vite, React Router | 사용자 화면, 라우팅, 티켓 작업 공간 |
| Backend | Python 3.11, FastAPI, Pydantic, SQLAlchemy | API 서버, 워크플로우 조정, 데이터 처리 |
| Database | PostgreSQL 15 | 티켓, 승인, 감사 로그, 보고서 버전, 채팅 기록 저장 |
| Vector DB | Milvus 2.4.23 | RAG 기반 근거 검색 |
| RAG Infrastructure | MinIO, etcd | Milvus 로컬 실행 구성 |
| AI Integration | OpenAI-compatible client | 보고서 초안 생성, 근거 기반 채팅, LLM 보조 수정 |
| Runtime | Docker, Docker Compose | 백엔드, 데이터베이스, RAG 인프라 실행 |
| Validation | pytest, ESLint, TypeScript build | 백엔드 테스트, 프론트엔드 정적 검사 및 빌드 |

## Getting Started

### Backend

```powershell
cd pillioo\backend
Copy-Item .env.example .env
docker compose up -d postgres fastapi
```

RAG 기반 근거 검색까지 실행하려면 Milvus, MinIO, etcd를 함께 실행합니다.

```powershell
cd pillioo\backend
docker compose --profile rag up -d etcd minio milvus
```

### Frontend

```powershell
cd pillioo-client
npm install
npm run dev
```

### Validation

```powershell
cd pillioo\backend
pytest
```

```powershell
cd pillioo-client
npm run lint
npm run build
```

## Team Roles

| Name | Role | Contributions | Contact |
|---|---|---|---|
| 김지민 | PM, AI Lead & FE | Product planning, RAG pipeline, evidence sufficiency evaluation, AI orchestration, retrieval evaluation, frontend development | jimni3155@sookymung.ac.kr |