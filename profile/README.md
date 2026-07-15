<img width="1680" height="1478" alt="image" src="https://github.com/user-attachments/assets/c04fc363-67ad-451c-8a96-49435e558e86" />

Pillioo는 의약품 리콜 및 안전 이벤트 대응을 돕는 약사 중심 의사결정 지원 시스템입니다.

외부 리콜 정보, 내부 재고 데이터, 근거 문서, AI 보고서 초안, 약사 검토, 승인 이력, 감사 로그를 하나의 워크플로우로 연결합니다. 시스템은 최종 판단을 자동으로 내리지 않으며, 약사 또는 권한 있는 담당자의 검토를 전제로 합니다.

이 프로젝트는 리콜 이벤트가 들어온 뒤 내부 재고와 영향을 비교하고, 관련 근거를 검색한 다음, 검토 가능한 보고서 초안을 생성하는 흐름을 구현했습니다.

## Preview
<img width="1458" height="582" alt="image" src="https://github.com/user-attachments/assets/e58623f0-d4fa-454b-b40f-f49b78a522ce" />
<img width="1436" height="590" alt="image" src="https://github.com/user-attachments/assets/4626fb4c-98f1-487e-9a1e-624022fca3d7" />
<img width="1456" height="576" alt="image" src="https://github.com/user-attachments/assets/9a3c3a51-a03c-4b63-bd31-0869bdb5349c" />
<img width="1420" height="584" alt="image" src="https://github.com/user-attachments/assets/f1ee56a7-1882-4448-9c67-b2bebaf2cd86" />
<img width="1474" height="586" alt="image" src="https://github.com/user-attachments/assets/075b03da-f47b-446a-8b8c-c14503128bf0" />
<img width="1462" height="592" alt="image" src="https://github.com/user-attachments/assets/e722c23c-c68c-4803-bfbd-8dd5720ee6e2" />
<img width="1414" height="590" alt="image" src="https://github.com/user-attachments/assets/8fa30fa9-f5f2-490c-866c-6830ad16581a" />


## Demo



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
| 김지민 | PM & AI Lead | Product planning, frontend development, <br> RAG pipeline, evidence sufficiency evaluation,<br>AI orchestration and retrieval evaluation | [jimni3155@sookmyung.ac.kr](mailto:jimni3155@sookmyung.ac.kr) |
