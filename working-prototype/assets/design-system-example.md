# 디자인시스템: 거래소 A (가상 디지털자산 거래소)

> **작성 예시** — `design-system.md` 템플릿을 실제로 채운 인스턴스. 원본: `~/Desktop/파라파라나춰야지/design-system-exchange-a.md` (그쪽이 최신이면 그쪽을 따른다).
> 라이트 테마 단일 (다크모드 없음 — 팀 결정 2026-06-11).
> 토큰 출처: shadcn/ui preset (base=base, **style=rhea**, baseColor=zinc, **theme=indigo**, font=inter, radius=default)의
> 라이트 모드 CSS 변수를 hex로 변환해 차용. 런타임은 shadcn을 쓰지 않으며(의존성 0 계약 유지),
> 단일 HTML 안에서 아래 변수 네이밍 그대로 인라인 CSS로 구현한다. rhea 스타일 = 면(filled) 위주·보더 최소·radius 큼.

## 1. Color (색)

라이트 테마 단일. CSS 변수 네이밍은 shadcn 컨벤션을 따른다.

**중립 (zinc 스케일)**
- **Background** `--background: #ffffff` — 페이지 기본 바탕
- **Surface(sidebar/보조 영역)** `--surface: #fafafa` — 사이드 영역·구분 배경
- **Card / Popover** `#ffffff` + border로 구분 (그림자 최소)
- **Text 본문** `--foreground: #09090b` (zinc-950)
- **Text 보조** `--muted-foreground: #71717a` (zinc-500)
- **Text 비활성** `#a1a1aa` (zinc-400)
- **Muted/Secondary 배경** `--muted: #f4f4f5` (zinc-100), 그 위 텍스트 `#18181b` (zinc-900)
- **Border** `--border: #e4e4e7` (zinc-200)
- **Input 면** `--input: #e4e4e7` (zinc-200) — 인풋 배경에 **50% 투명도**로 사용 (rhea 면 스타일, 보더 없음)
- **Focus ring** `--ring: #a1a1aa` (zinc-400) — 포커스는 브랜드색이 아니라 ring 색: 1px 보더 + 바깥 3px 링(30% 투명)

**브랜드**
- **Primary** `--primary: #4338ca` (indigo-700) — 주 액션 버튼, 활성 탭, 링크. 한 화면에 주 액션 1개 원칙.
- **Primary 위 텍스트** `--primary-foreground: #eef2ff` (indigo-50)

**Semantic**
- success `#16a34a` (green-600) / warning `#d97706` (amber-600) / error·destructive `#dc2626` (red-600) / info `#2563eb` (blue-600)

**시세 색 (거래소 도메인 필수)**
- **상승** `--price-up: #d93b43` — 국내 거래소 관례: 상승=빨강
- **하락** `--price-down: #1373e8` — 하락=파랑
- 두 색 모두 흰 바탕 대비 **4.5:1 이상**(WCAG AA, 본문 크기까지 안전). 지정 원본(#dd3c44/#1375ec, 대비 4.4:1)을 색감 유지한 채 2% 미만 어둡게 보정한 값.
- **보합** `#71717a` (zinc-500)
- 시세 색은 숫자·등락 아이콘에만. 배경 면적 채색은 호가창 잔량 바 정도로 제한.

**차트 (indigo 단색 계열)**
- chart-1 `#a5b4fc` / chart-2 `#6366f1` / chart-3 `#4f46e5` / chart-4 `#4338ca` / chart-5 `#3730a3`
- 단, 캔들 차트는 위 시세 색(상승 빨강/하락 파랑)을 따른다.

## 2. Typography (타이포)

- **Font family**: `Inter, -apple-system, "Apple SD Gothic Neo", "Malgun Gothic", system-ui, sans-serif`
  — 의존성 0 계약상 웹폰트 로드 금지. Inter는 설치돼 있으면 쓰고 없으면 시스템 폰트로 자연 폴백. 헤딩 = 본문과 동일 패밀리(preset의 fontHeading=inherit).
- **Scale** (line-height / weight):
  - display 28px / 1.25 / 700 — 자산 총액 등 핵심 수치
  - h1 22px / 1.3 / 700
  - h2 18px / 1.4 / 600
  - h3 16px / 1.45 / 600
  - body 14px / 1.5 / 400
  - caption 12px / 1.4 / 400 (`#71717a`)
- **숫자/금액 표기**:
  - 모든 수치에 `font-variant-numeric: tabular-nums` (목록 정렬 흔들림 방지)
  - KRW는 정수 + 천단위 콤마 (`52,341,000`), 단위는 숫자 뒤 "원" 또는 "KRW" 중 화면당 하나로 통일
  - 코인 수량은 유효 소수점만 표시하되 같은 컬럼 안에서는 자릿수 통일
  - **금액은 절대 반올림·축약("5,234만") 표기하지 않는다** (요약 위젯 예외, 그때도 정확값 툴팁 제공)
  - 등락률은 부호 포함 소수 둘째 자리: `+2.41%` / `-0.87%`

## 3. Spacing (간격)

- **Base unit**: 4px
- **Scale**: xs 4 / sm 8 / md 12 / lg 16 / xl 24 / 2xl 32
- **컨테이너 패딩**: 모바일 16px, 카드 내부 16px
- **섹션 간격**: 24px, 리스트 행 높이: 최소 48px (터치 타깃)

## 4. Layout (레이아웃)

- **모바일 우선**, 기준 폭 375px. 데스크탑 분기점 768px (프로토타입은 375px 고정 프레임으로 충분)
- **화면 골격**: 상단바(타이틀+우측 액션) → 콘텐츠 스크롤 영역 → 하단 탭바(5탭) 고정
- **Radius**: base 10px (`0.625rem`, preset 값). sm 6px(작은 칩) / lg 14px(모달·시트) / **xl 16px(버튼·인풋 등 컨트롤 — rhea `rounded-2xl`)**
- **Elevation**: 라이트 테마라 그림자 대신 **border 우선**. 그림자는 2단계만 —
  - overlay: `0 4px 12px rgb(0 0 0 / 0.08)` (모달·바텀시트)
  - raised: `0 1px 2px rgb(0 0 0 / 0.05)` (드물게, 플로팅 요소)

## 5. Components (컴포넌트)

- **Button** (rhea: 면 위주·보더 없음): 높이 48px(주요)/36px(보조 — rhea 원본 32/36의 모바일 적응값), **radius 16px(xl)**
  - primary: bg `#4338ca` / text `#eef2ff` / hover·pressed는 80% 불투명도
  - secondary: bg `#f4f4f5` / text `#18181b`
  - ghost: 투명 bg / text **중립 `#09090b`** (hover 시 muted 면) — 브랜드색 텍스트 버튼은 link 용도로만
  - disabled: 별도 회색이 아니라 **해당 스타일 그대로 50% 투명도**
  - 커서: 클릭 가능 요소는 `cursor: pointer` (preset의 --pointer 반영)
- **Input** (rhea 면 스타일): 높이 48px(모바일 적응값), **보더 없음**, bg `--input` 50%, **radius 16px(xl)**
  - focus: ring 색(`#a1a1aa`) 1px 보더 + 바깥 3px 링(30%) — 브랜드색 아님
  - error: border `#dc2626` 1px + 바깥 3px 링(20%) + 하단 12px 헬퍼 텍스트
  - disabled: 전체 50% 투명도
- **Card / List item**: 카드 = white bg + border. 리스트 행 = border-bottom `#f4f4f5`, 좌측 정보·우측 수치(우측 정렬, tabular-nums)
- **Navigation**: 하단 탭바 5탭(높이 56px, 활성 `#4338ca`/비활성 `#a1a1aa`), 상단바 56px
- **거래소 특화**:
  - **호가창**: 매수/매도 잔량 바는 시세 색 8% 투명도 배경, 숫자는 진한 시세 색
  - **시세 리스트 행**: 코인명/심볼 — 현재가 — 등락률(시세 색) 3컬럼
  - **토스트**: 하단 탭바 위 16px, zinc-900 bg + white text, 3초 자동 소멸
  - **바텀시트**: radius-lg 상단 모서리, 딤 `rgb(0 0 0 / 0.4)`

## 6. Motion (모션)

- **Duration**: fast 120ms (hover/pressed) / base 200ms (시트·토스트 등장) / slow 320ms (화면 전환)
- **Easing**: `cubic-bezier(0.2, 0, 0, 1)` (감속 위주)
- **원칙**: 전환·피드백에만 움직인다. 장식 애니메이션 금지. **시세 숫자 변동에 깜빡임·플래시 효과 금지** (실데이터가 아닌 프로토타입에서 가짜 생동감 연출은 정직성 규율 위반).

## 7. Voice (보이스 · 마이크로카피)

- **톤**: 간결한 해요체. 친근하되 호들갑 없음 — 돈을 다루는 화면에서는 정확함이 친절함.
- **버튼**: 동사로 끝나는 행동 명령형 — "입금하기", "주문하기". "확인" 같은 무의미 레이블 지양.
- **에러**: 원인 + 다음 행동을 한 문장씩 — "네트워크 연결이 불안정해요. 잠시 후 다시 시도해 주세요."
- **빈 상태**: 상황 설명 + 행동 유도 1개 — "아직 보유한 자산이 없어요" + [입금하기]
- **금지**: 과장("대박", "긴급"), 공포 소구, 책임 회피형 문구("~일 수 있습니다"의 남용)
- **선호**: 수치는 문장보다 숫자로 직접 제시

## 8. Brand (브랜드)

- **인상 한 문장**: "숫자가 또렷하게 읽히는, 군더더기 없는 밝은 거래소"
- **포지셔닝**: 흰 바탕 + zinc 중립 + 절제된 indigo 포인트. 색은 정보(시세·상태)에 양보하고 브랜드는 타이포와 여백으로 말한다. indigo는 시세 파랑(blue)과 색상환에서 떨어져 있어 "브랜드 색 ≠ 시세 색"이 한눈에 구분된다.
- **로고**: 사용하지 않는다. 좌상단 워드마크는 "거래소 A" 텍스트(weight 700)로 대체.

## 9. Anti-patterns (하지 말 것)

- **실존 거래소의 로고·브랜드 컬러·고유 카피를 복제하지 않는다.** 이 문서의 모든 토큰은 범용 오픈소스 팔레트(zinc/indigo) 기반이다. 파일명·주석·문서 어디에도 특정 거래소 실명을 쓰지 않는다.
- 다크 배경 사용 금지 — 이 제품은 라이트 단일 테마다. (오버레이 딤은 예외)
- Primary 버튼을 한 화면에 둘 이상 두지 않는다.
- 금액을 반올림·축약 표기하지 않는다.
- 시세 색(빨강/파랑)을 시세·상태 외 용도(장식, 강조)에 쓰지 않는다.
- 비활성 상태에 전용 색을 새로 칠하지 않는다 — 원래 스타일에 50% 투명도가 규칙(rhea). 비활성을 위해 브랜드 indigo를 더 진하게/다르게 쓰는 것 금지.
- 그림자를 깊이 표현의 기본 수단으로 쓰지 않는다 — border 우선.
- 웹폰트·외부 CSS·JS 라이브러리를 로드하지 않는다 (의존성 0 계약).
