# 이휘 · AI 서비스 개발자

LangGraph와 FastAPI로 자연어 요청을 분석하고, 필요한 정보를 확인하며, 다음 작업으로 연결하는 AI Workflow를 개발합니다.
Flutter 앱·웹 개발과 스토어 심사, 웹 배포, QA 경험도 있습니다.

[포트폴리오](https://iwhya.kr) · [FOWOCO 구현 사례](https://iwhya.kr/projects/hr-agent)

## 대표 프로젝트

| 프로젝트 | 해결하려는 문제 | 주요 기술 |
| --- | --- | --- |
| [FOWOCO](projects/fowoco.md) | 외국인근로자 HR 업무에서 누락 정보와 서류 상태를 확인하고 다음 절차를 연결 | Python, FastAPI, LangGraph |
| [Hwiya IoT](https://github.com/EHWIYA/home-assistant-front-end) | 에어컨·콘센트·멀티탭 상태 조회와 제어를 모바일 화면에 통합 | React, TypeScript, FastAPI, PWA |
| [Ledger Weight](https://github.com/EHWIYA/ledger-weight-back-end) | 카드 게임의 실시간 통신과 게임 로직을 백엔드 서버로 구현 | Python, FastAPI, WebSocket |

## FOWOCO에서 맡은 일

**8인 교육 팀 프로젝트 · 2026.06–2026.08 · Agent Orchestration / AI Serving**

재계약·체류기간 연장 업무를 지원하는 서비스에서 Supervisor Graph와 Shared State, AI Serving API를 담당했습니다.
AI가 요청을 분석하고 초안을 만들면, HR 담당자가 검토하고 최종 승인하는 구조입니다.

- **계획과 분석 분리:** AI가 필요한 데이터 항목을 먼저 요청하고, Server가 권한을 확인해 값을 보충한 뒤 분석하도록 API를 구성했습니다. [PR #13](https://github.com/fowoco/ai/pull/13)
- **서류 누락 분기:** 여권·외국인등록증 상태가 `MISSING`이면 근로자에게 서류를 요청하도록 연결했습니다. [PR #27](https://github.com/fowoco/ai/pull/27)
- **실행 모델 추적:** 분석 응답에 실제 Intent 모델 정보를 반환해 모델 실행과 fallback을 구분하도록 수정했습니다. [PR #28](https://github.com/fowoco/ai/pull/28)

[개인 기여 상세](projects/fowoco.md) · [팀 AI Runtime](https://github.com/fowoco/ai) · [팀 역할 소개](https://github.com/fowoco#team-contributions)

## 기술과 경험

- **AI Workflow:** Python, FastAPI, LangGraph — 요청 분석, 상태 관리, 조건별 분기와 API 연동
- **앱·웹:** Dart, Flutter, React, TypeScript — 화면 개발, API 연동, 배포와 QA
- **개발·검증:** Git, Docker, GitHub Actions, Pytest — 변경 검토, 실행 환경 구성과 테스트

