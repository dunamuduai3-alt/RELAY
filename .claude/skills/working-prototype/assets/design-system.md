# 디자인시스템: <브랜드/제품명>

> 이 문서는 프로토타입의 시각·상호작용 규칙을 담는 **단일 진실 원천(single source of truth)**입니다.
> `working-prototype` 스킬은 이 9개 섹션을 토큰처럼 읽어 HTML을 생성합니다. 비어 있는 칸은 추측으로 채우지 말고 "미정"으로 두세요 — 미정인 채로 두면 스킬이 합리적 기본값을 쓰고 그 사실을 명시합니다.

## 1. Color (색)
- **Primary**: `#______` — 주 액션·브랜드. 어디에 쓰는지 한 줄.
- **Secondary / Accent**: `#______`
- **Background**: 표면 단계별 (`bg`, `surface`, `elevated`) `#______`
- **Text**: 본문 / 보조 / 비활성 `#______`
- **Semantic**: success / warning / error / info `#______`
- 다크모드 있으면 위를 라이트/다크 한 쌍으로.

## 2. Typography (타이포)
- **Font family**: 본문 / 헤딩 / 모노 (웹폰트면 출처)
- **Scale**: display / h1 / h2 / h3 / body / caption — size·line-height·weight
- **숫자/금액 표기 규칙**: (금융 앱이면 중요 — 천단위, 정렬, tabular-nums 등)

## 3. Spacing (간격)
- **Base unit**: `__px` (보통 4 또는 8)
- **Scale**: xs / sm / md / lg / xl = 몇 px
- **컨테이너 패딩 · 섹션 간격**의 기본값

## 4. Layout (레이아웃)
- **Grid / breakpoint**: 모바일 우선이면 기준 폭(예: 375px), 데스크탑 분기점
- **주요 화면 골격**: 헤더 / 탭바 / 콘텐츠 영역 구조
- **Radius · Elevation(그림자)** 단계

## 5. Components (컴포넌트)
핵심 UI 요소의 모양·상태를 정의. 프로토타입이 이걸 그대로 재현합니다.
- **Button**: primary / secondary / ghost — 크기, 상태(default/hover/pressed/disabled)
- **Input / Field**: 기본, 포커스, 에러
- **Card / List item**
- **Navigation**: 탭바 / 상단바 / 모달
- (앱 특성상 핵심인 컴포넌트 추가 — 예: 차트, 호가창, 토스트)

## 6. Motion (모션)
- **Duration**: fast / base / slow = 몇 ms
- **Easing**: 기본 커브
- **언제 움직이고 언제 안 움직이는가**: 전환·피드백에만, 장식 애니메이션 자제 등

## 7. Voice (보이스 · 마이크로카피)
- **톤**: 격식체/반말, 친근/전문적
- **버튼·에러·빈 상태 문구**의 말투 원칙과 예시
- 금지 표현 / 선호 표현

## 8. Brand (브랜드)
- 이 제품이 주는 **인상 한 문장**(예: "빠르고 신뢰감 있는, 군더더기 없는")
- 경쟁/레퍼런스 대비 시각적 포지셔닝
- 로고·아이콘 사용 규칙(있으면)

## 9. Anti-patterns (하지 말 것)
프로토타입에서 **절대 하지 말아야 할 것**을 명시. 이 섹션이 품질을 지킵니다.
- 예: "Primary 버튼을 한 화면에 둘 이상 두지 않는다"
- 예: "금액은 절대 반올림 표시하지 않는다"
- 예: "브랜드 색을 비활성 상태에 쓰지 않는다"
