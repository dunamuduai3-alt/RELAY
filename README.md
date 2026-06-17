# RELAY — UX Skill Pipeline

UX 업무를 **단계별 AI 스킬**로 쪼갠 선형 파이프라인. 각 스킬의 출력이 다음 스킬의 입력이 되는 **"산출물 계약(output contract)"** 이 핵심입니다.

> 기성 툴을 쓰는 게 아니라, **업무 도구(스킬)까지 직접 만들었다** — 거래소 A · KYC(고객확인) 재이행 해커톤 산출물.

## 🔗 관련

- **프로토타입 데모 (AS-IS vs TO-BE):** https://relay-kyc.vercel.app
- **프로젝트 소개 슬라이드 (deck):** https://relay-deck.vercel.app
- **파이프라인 노하우:** [`노하우.md`](노하우.md) — 단계별 노하우 + 바로 복붙 가능한 프롬프트

## 🧩 6단계 파이프라인

| 단계 | 스킬 | 하는 일 | 산출물 |
|---|---|---|---|
| ① 문제 발굴 | [`review-mining`](.claude/skills/review-mining/) | 구글플레이·네이버 카페·디시·VOC 마이닝 → 개인정보 마스킹 → 빈도×심각도 군집 | 웹 리포트 + raw CSV + PRD 핸드오프 |
| ② PRD 작성 | [`product-brief`](.claude/skills/product-brief/) | 사용자 증거에서 "문제 정의 → 해결 가설" 정리 | 문제 브리프 / PRD (md) |
| ③ 벤치마크 | [`design-reference`](.claude/skills/design-reference/) | 실제 앱 스크린샷·아티클 리서치 | 코멘트 붙은 레퍼런스 보드 |
| ④ 와이어프레임 N종 | [`design-variants`](.claude/skills/design-variants/) | 서로 다른 UX 가설 N종(기본 3)으로 시안 분기 | 가설 카드 + 분기 매트릭스 + 비교 보드 |
| ⑤ 돌아가는 프로토타입 | [`working-prototype`](.claude/skills/working-prototype/) | PRD·와이어·DS → 클릭되는 단일 HTML | 의존성 0 인터랙티브 프로토타입 |
| ⑥ 스냅 & UX Lint | [`snap-ux-lint`](.claude/skills/snap-ux-lint/) | Nielsen 10 휴리스틱으로 화면/플로우 린트 | 플로우·화면 UX Lint 리포트 + 주석 스냅샷 |

## 품질 기준

모든 화면·플로우는 **Nielsen Norman Group 10 Usability Heuristics** 기준으로 린트합니다.

## 전제 (Requirements)

- **[Claude Code](https://claude.com/claude-code)** — 스킬은 Claude Code가 트리거 문장을 인식해 자동 호출합니다.
- `review-mining`·`snap-ux-lint`는 `agents/openai.yaml`이 있어 **Codex에서도** 호출 가능합니다.
- `design-reference`는 실제 앱 스크린샷 수집에 **Lazyweb MCP**를 사용합니다.

## 구조

스킬은 Claude Code 관례대로 [`.claude/skills/`](.claude/skills/)에 들어 있고, 각 스킬은 `SKILL.md`(정의) + 보조 자산(`assets/`·`references/`·`agents/`)으로 구성됩니다.

## 사용 — 트리거 문장

정확한 명령어가 아니라 자연어로 부르면 해당 스킬이 발동합니다.

| 스킬 | 이렇게 부르면 발동 |
|---|---|
| `review-mining` | "이 리뷰에서 페인포인트 뽑아줘", "리뷰 분석해서 기획거리" |
| `product-brief` | "문제 정의해줘", "PRD 써줘", "프로덕트 브리프 써줘" |
| `design-reference` | "레퍼런스 찾아줘", "다른 앱들은 이 화면 어떻게 했어?" |
| `design-variants` | "시안 3종 뽑아줘", "방향 갈라보자", "A안 B안 C안" |
| `working-prototype` | "돌아가는 프로토타입 만들어줘", "클릭되는 목업" |
| `snap-ux-lint` | "이 화면 UX 점검해줘", "휴리스틱으로 린트해줘" |

단계별 **바로 복붙 가능한 프롬프트**는 [`노하우.md`](노하우.md)에 정리돼 있습니다.
