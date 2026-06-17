# RELAY — UX Skill Pipeline

UX 업무를 **단계별 AI 스킬**로 쪼갠 선형 파이프라인. 각 스킬의 출력이 다음 스킬의 입력이 되는 **"산출물 계약(output contract)"** 이 핵심입니다.

> 기성 툴을 쓰는 게 아니라, **업무 도구(스킬)까지 직접 만들었다** — 거래소 A · KYC(고객확인) 재이행 해커톤 산출물.

## 🔗 관련

- **프로토타입 데모(Vercel):** https://relay-kyc.vercel.app
- **프로토타입 소스:** [`prototype/`](prototype/) — 데모 랜딩(`index.html` = AS-IS vs TO-BE 비교), 기존 메뉴(`menu.html`), 프로토타입 5종(`prototypes/`)
- **프로젝트 소개 슬라이드:** https://relay-deck.vercel.app

## 🧩 파이프라인 (원래 7단계 → 6단계, 7번 AS-IS/TO-BE는 백로그)

| 단계 | 스킬 | 하는 일 | 산출물 |
|---|---|---|---|
| ① 문제 발굴 | [`review-mining`](review-mining/) | 구글플레이·네이버 카페·디시·VOC 마이닝 → 개인정보 마스킹 → 빈도×심각도 군집 | 웹 리포트 + raw CSV + PRD 핸드오프 |
| ② PRD 작성 | [`product-brief`](product-brief/) | 사용자 증거에서 "문제 정의 → 해결 가설" 정리 | 문제 브리프 / PRD (md) |
| ③ 벤치마크 | [`design-reference`](design-reference/) | 실제 앱 스크린샷·아티클 리서치 | 코멘트 붙은 레퍼런스 보드 |
| ④ 와이어프레임 N종 | [`design-variants`](design-variants/) | 서로 다른 UX 가설 N종(기본 3)으로 시안 분기 | 가설 카드 + 분기 매트릭스 + 비교 보드 |
| ⑤ 돌아가는 프로토타입 | [`working-prototype`](working-prototype/) | PRD·와이어·DS → 클릭되는 단일 HTML | 의존성 0 인터랙티브 프로토타입 |
| ⑥ 스냅 & UX Lint | [`snap-ux-lint`](snap-ux-lint/) | Nielsen 10 휴리스틱으로 화면/플로우 린트 | 플로우·화면 UX Lint 리포트 + 주석 스냅샷 |

## 실행 방식

- **Phase 1** — 앞 단계 출력 없이 가능한 스킬/템플릿을 **병렬 제작**
- **Phase 2** — 실제 케이스 1개를 ①→⑥ 순차로 돌리며 디벨롭

UX Guide 기준: **Nielsen Norman Group 10 Usability Heuristics**.

## 구조

각 스킬은 `SKILL.md`(정의) + 보조 자산(`assets/`·`references/`·`agents/`)으로 구성됩니다.
`review-mining`·`snap-ux-lint`는 `agents/openai.yaml`로 Codex에서도 호출 가능합니다.
