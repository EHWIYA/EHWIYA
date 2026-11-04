# FOWOCO · 개인 기여

외국인근로자를 고용한 사업장의 재계약·체류기간 연장 업무를 지원하는 AI 업무보조 서비스입니다.

**KT AIVLE School 교육 팀 프로젝트 · 8인 · 2026.06.29–2026.08.26**  
**담당: Agent Orchestration / AI Serving**

[구현 사례](https://iwhya.kr/projects/hr-agent) · [팀 프로젝트](https://github.com/fowoco) · [AI Runtime](https://github.com/fowoco/ai)

## 해결하려는 문제

HR 담당자는 업무를 처리할 때 근로자 정보와 기한, 서류 보유 여부를 함께 확인해야 합니다.
필수 정보나 서류가 빠졌을 때 추가 질문과 서류 요청이 이어지도록 AI Workflow를 구성했습니다.

## 담당 범위

LangGraph 기반 Supervisor Graph와 Shared State, 조건별 Workflow 라우팅, AI Serving API를 담당했습니다.
중단 지점을 저장하고 정보를 보완한 뒤 작업을 재개하는 흐름도 구성했습니다.

Intent 모델 학습, OCR 인식 파이프라인, 언어·문서 생성 도구는 팀원들의 담당 영역입니다.
제 기여는 이 도구의 결과와 업무 상태를 Workflow에 연결하고 다음 단계를 결정하는 부분입니다.

## 주요 변경과 근거

| 변경 | 이전 동작 또는 문제 | 반영 내용 | 근거 |
| --- | --- | --- | --- |
| PLAN / ANALYZE 분리 | 분석 전에 Server에서 필요한 정보를 보충하는 흐름 필요 | PLAN에서 필요한 키를 요청하고, 값이 채워진 ANALYZE에서 후속 경로 결정 | [병합 PR #13](https://github.com/fowoco/ai/pull/13) |
| 서류 상태에 따른 분기 | 문서번호나 업로드 파일만으로 서류 보유 여부 추측 | Server의 `MISSING`, `SUBMITTED`, `VERIFIED` 상태를 반영하고 누락 시 `ask_worker`로 분기 | [병합 PR #27](https://github.com/fowoco/ai/pull/27) |
| 실제 Intent 모델 정보 반환 | 분석 응답의 모델 정보가 `stub` 기본값으로 반환 | 실제 모델과 fallback 메타데이터를 응답에 연결 | [병합 PR #28](https://github.com/fowoco/ai/pull/28) |

## 설계에서 구분한 책임

AI Runtime은 분석 결과와 문서 초안을 반환합니다.
Server는 인증·권한과 공식 업무 상태를 관리하고, HR 담당자가 최종 판단과 승인을 수행합니다.

서류 누락 시에는 근로자 요청으로, 정보가 부족한 경우에는 보완 질문으로 연결합니다.
OCR·언어·문서 도구의 담당 범위를 유지하면서 필요한 결과를 Workflow State로 전달합니다.

## 검증 자료를 읽는 방법

위 PR은 모두 EHWIYA 작성 및 병합 상태를 확인한 공개 구현 근거입니다.
PR #27과 #28에는 관련 테스트 통과와 당시 전체 테스트의 기존 실패가 함께 기록돼 있습니다.
이 문서 정리 과정에서는 코드를 실행하거나 테스트를 다시 수행하지 않았습니다.
구현 및 변경 당시의 테스트 기록과 실제 HR 업무에서의 효과는 구분해 평가해야 합니다.

[팀의 개인별 기여](https://github.com/fowoco#team-contributions) · [팀 Runtime 실행·검증 안내](https://github.com/fowoco/ai#readme)

