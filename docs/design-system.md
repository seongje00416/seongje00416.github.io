# Design System

seongje00416.github.io 포트폴리오 사이트의 디자인 시스템 문서입니다.
Tailwind CSS 기반의 다크 모드 전용 디자인을 사용합니다.

---

## 목차

1. [색상 (Colors)](#색상)
2. [타이포그래피 (Typography)](#타이포그래피)
3. [간격 (Spacing)](#간격)
4. [레이아웃 (Layout)](#레이아웃)
5. [컴포넌트 (Components)](#컴포넌트)
6. [인터랙션 (Interaction)](#인터랙션)
7. [아이콘 (Icons)](#아이콘)
8. [배경 효과 (Background Effects)](#배경-효과)

---

## 색상

### 커스텀 색상 토큰 (Tailwind Config)

| 토큰 | 값 | 용도 |
|---|---|---|
| `primary` | `#13ec37` | 브랜드 강조색 (네온 그린) |
| `background-dark` | `#0a0c10` | 메인 배경 (딥 차콜) |
| `background-light` | `#f6f8f6` | 라이트 모드 배경 (미사용) |
| `accent-cloud` | `#2d2a4a` | 보조 강조 (뮤트 퍼플-블루) |

### Slate 팔레트 (텍스트 및 UI)

| 클래스 | 용도 |
|---|---|
| `text-white` / `text-slate-100` | 주요 헤딩, 강조 텍스트 |
| `text-slate-300` | 일반 본문 텍스트 |
| `text-slate-400` | 보조 텍스트 |
| `text-slate-500` | 비활성/힌트 텍스트 |
| `text-slate-600` | 구분선, 메타 정보 |
| `bg-slate-800` | 카드 배경 |
| `bg-slate-900` | 카드/컨테이너 배경 (더 어두운) |
| `border-slate-800` | 기본 테두리 |
| `border-slate-700` | 강조 테두리 |

### Primary 투명도 변형

```
bg-primary/10   → 배지 배경, 태그 배경
bg-primary/20   → 아이콘 컨테이너 배경
bg-primary/50   → 진한 강조 배경
bg-primary/90   → 반투명 버튼 배경
border-primary/30 → 카드 hover 테두리
border-primary/50 → 강한 hover 테두리
text-primary    → 링크, 강조 텍스트, 레이블
```

---

## 타이포그래피

### 폰트

- **패밀리**: `Inter` (Google Fonts, sans-serif)
- **Tailwind 토큰**: `font-display`

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;900&display=swap" rel="stylesheet">
```

### 타입 스케일

| 역할 | 클래스 | 설명 |
|---|---|---|
| Hero H1 | `text-5xl md:text-7xl font-black tracking-tight` | 히어로 섹션 메인 제목 |
| Page H2 | `text-3xl font-black` | 섹션 헤더 |
| Card H3 | `text-xl lg:text-2xl font-bold` | 카드 제목 |
| Subheading | `text-lg font-semibold` | 소제목 |
| Body | `text-sm` ~ `text-base` | 본문 |
| Label | `text-xs uppercase tracking-widest font-bold` | 섹션 레이블, 배지 |
| Caption | `text-xs text-slate-500` | 캡션, 메타 |

### 자간 (Letter Spacing)

| 클래스 | 용도 |
|---|---|
| `tracking-tight` | 대형 헤딩 |
| `tracking-wider` | 일반 강조 |
| `tracking-widest` | 레이블, 배지 텍스트 |

### 행간 (Line Height)

| 클래스 | 용도 |
|---|---|
| `leading-tight` | 헤딩 |
| `leading-relaxed` | 본문 단락 |

---

## 간격

### 페이지 기본 여백

```
모바일: px-6  (24px)
데스크탑: lg:px-20  (80px)
```

### 섹션 패딩

```
세로: py-16, py-20
상단: pt-16  (헤더 오프셋)
```

### Gap 스케일

| 값 | 사용 맥락 |
|---|---|
| `gap-2` | 인라인 요소 (아이콘 + 텍스트) |
| `gap-3` | 작은 배지 그룹 |
| `gap-4` | 카드 내부 항목 |
| `gap-6` | 카드 그리드 |
| `gap-8` | 섹션 내 블록 |
| `gap-10` | 2컬럼 레이아웃 |
| `gap-12` | 섹션 간격 |

### Margin 스케일

```
mb-2, mb-4, mb-6, mb-8, mb-12  (하단 여백)
mt-4, mt-8, mt-10, mt-24        (상단 여백)
```

---

## 레이아웃

### 최대 너비

```
max-w-6xl mx-auto  → 모든 페이지 콘텐츠 컨테이너
w-full              → 전체 너비 섹션
```

### 그리드 시스템

| 패턴 | 클래스 |
|---|---|
| 프로젝트 카드 | `grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6` |
| 기술 스택 | `grid grid-cols-2 lg:grid-cols-4 gap-4` |
| 스킬 아이콘 | `grid grid-cols-3 lg:grid-cols-5 gap-4` |
| 2컬럼 | `grid md:grid-cols-2 gap-10` |

### Flex 패턴

```
헤더:    flex items-center justify-between
히어로:  flex flex-col items-center text-center gap-8
카드 내: flex items-center gap-3
모바일 → 데스크탑: flex-col md:flex-row
```

### 헤더 (Navigation)

```css
/* 스타일 */
position: fixed (z-50)
border-b: border-slate-800/50
padding: px-6 py-4 lg:px-20
background: bg-background-dark/80 backdrop-blur-md

/* 구성 */
[로고 + 이름] ─── [네비게이션 링크] ─── [GitHub 버튼]
                 (hidden md:flex)
```

---

## 컴포넌트

### 카드 (Card)

```html
<div class="bg-slate-900/40 border border-slate-800 rounded-2xl p-6
            hover:border-primary/30 transition-all duration-300">
  ...
</div>
```

**변형:**
- `rounded-2xl` → 일반 카드
- `rounded-3xl` → 대형 카드 (히어로 섹션)
- `bg-slate-900/40` → 기본 반투명 배경
- `bg-slate-800/50` → 진한 배경

---

### 버튼 (Button)

**Primary 버튼**
```html
<a class="bg-primary text-background-dark px-5 py-2 rounded-lg font-bold
          hover:bg-primary/90 transition-colors duration-200">
  버튼 텍스트
</a>
```

**Secondary / Outline 버튼**
```html
<a class="border border-primary/30 text-primary px-5 py-2 rounded-lg font-bold
          hover:bg-primary/5 transition-colors duration-200">
  버튼 텍스트
</a>
```

**Ghost 버튼 (GitHub)**
```html
<a class="flex items-center gap-2 border border-slate-700 text-slate-300
          px-4 py-2 rounded-lg hover:bg-slate-800/50 transition-colors duration-200">
  <img src="..." class="w-4 h-4"> GitHub
</a>
```

---

### 배지 / 태그 (Badge)

**Primary 배지 (강조)**
```html
<span class="px-3 py-1 bg-primary/10 border border-primary/30 text-primary
             rounded-full text-xs font-bold uppercase tracking-wider">
  라벨
</span>
```

**기술 스택 태그**
```html
<span class="px-3 py-1 bg-slate-200 dark:bg-primary/10 text-slate-700
             dark:text-slate-300 rounded text-sm">
  기술명
</span>
```

**상태 인디케이터 (Ping)**
```html
<span class="relative flex h-2 w-2">
  <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-primary opacity-75"></span>
  <span class="relative inline-flex rounded-full h-2 w-2 bg-primary"></span>
</span>
```

---

### 섹션 레이블 (Section Label)

```html
<p class="text-xs uppercase tracking-widest text-primary font-bold">
  섹션 이름
</p>
```

---

### 아이콘 컨테이너

```html
<div class="w-12 h-12 bg-primary/20 rounded-xl flex items-center justify-center">
  <span class="material-symbols-outlined text-primary">icon_name</span>
</div>
```

---

### 타임라인 (Timeline)

```html
<!-- 수직 라인 -->
<div class="absolute left-0 top-0 bottom-0 w-px bg-slate-800"></div>

<!-- 타임라인 마커 -->
<div class="absolute left-0 top-6 w-3 h-3 rounded-full bg-primary -translate-x-1/2"></div>

<!-- 아이템 -->
<div class="pl-8 pb-10 relative">
  ...
</div>
```

---

### 네비게이션 드롭다운

```html
<!-- 트리거 그룹 -->
<div id="blog-nav-group" class="relative group">
  <button class="flex items-center gap-1 text-slate-400 hover:text-primary">
    Blog <span class="material-symbols-outlined text-sm">expand_more</span>
  </button>

  <!-- 드롭다운 -->
  <div id="blog-dropdown"
       class="absolute top-full left-0 mt-2 w-40 bg-slate-900 border border-slate-800
              rounded-xl shadow-lg z-50 opacity-0 invisible transition-all duration-200">
    <a class="block px-4 py-3 text-sm text-slate-400 hover:text-primary hover:bg-slate-800/50">링크</a>
  </div>
</div>
```

JavaScript: 300ms 지연 후 숨김 처리 (마우스가 드롭다운으로 이동할 시간 확보)

---

## 인터랙션

### 호버 효과

| 효과 | 클래스 |
|---|---|
| 텍스트 컬러 변경 | `hover:text-primary transition-colors duration-200` |
| 카드 테두리 강조 | `hover:border-primary/30 transition-all duration-300` |
| 카드 살짝 올라가기 | `hover:border-primary/40 -translate-y-0.5` (`.card-hover`) |
| 스케일 업 | `hover:scale-105 transition-transform duration-200` |
| 배경색 변경 | `hover:bg-slate-800/50 transition-colors duration-200` |

### 트랜지션 기본값

```
transition-colors duration-200  → 색상 변화 (빠름)
transition-all duration-300     → 복합 변화 (보통)
transition-transform duration-200 → 변형 전용
```

### 애니메이션

```
animate-ping  → 상태 인디케이터 펄스 효과
```

---

## 아이콘

**Material Symbols Outlined** 사용

```html
<link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined" rel="stylesheet">
```

```html
<span class="material-symbols-outlined">icon_name</span>
```

**크기 제어:**
```
text-sm    → 작은 아이콘 (네비게이션)
text-base  → 기본 아이콘
text-xl    → 카드 내 아이콘
text-2xl   → 강조 아이콘
```

**주요 사용 아이콘:**
- `arrow_forward` — 링크/CTA
- `expand_more` — 드롭다운 화살표
- `open_in_new` — 외부 링크
- `code`, `terminal` — 기술 관련

---

## 배경 효과

### Cloud Gradient

```css
.cloud-gradient {
  background: radial-gradient(circle at 50% -20%, #1e1b33 0%, #0a0c10 70%);
}
```

히어로 섹션 상단에 부드러운 퍼플-블랙 그라데이션 효과를 부여합니다.

### Cloud Overlay

```css
.cloud-overlay {
  background-image: url('Google Cloud 이미지');
  opacity: 0.03;
}
```

`pointer-events-none`으로 클릭 방지, `z-0`으로 콘텐츠 아래 배치.

### 페이지 배경

```html
<body class="bg-background-dark font-display text-slate-300">
  <html class="dark">
```

---

## 빠른 참조: 자주 쓰는 패턴

### 새 카드 만들기

```html
<div class="bg-slate-900/40 border border-slate-800 rounded-2xl p-6 hover:border-primary/30 transition-all duration-300">
  <p class="text-xs uppercase tracking-widest text-primary font-bold mb-2">레이블</p>
  <h3 class="text-xl font-bold text-white mb-2">제목</h3>
  <p class="text-sm text-slate-400 leading-relaxed">설명</p>
</div>
```

### 새 섹션 만들기

```html
<section class="w-full max-w-6xl mx-auto px-6 lg:px-20 py-20">
  <p class="text-xs uppercase tracking-widest text-primary font-bold mb-2">섹션 레이블</p>
  <h2 class="text-3xl font-black text-white mb-8">섹션 제목</h2>
  <!-- 콘텐츠 -->
</section>
```

### Primary CTA 버튼

```html
<a href="#" class="inline-flex items-center gap-2 bg-primary text-background-dark px-5 py-2 rounded-lg font-bold hover:bg-primary/90 transition-colors duration-200">
  텍스트
  <span class="material-symbols-outlined text-sm">arrow_forward</span>
</a>
```
