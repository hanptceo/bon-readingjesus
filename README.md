# 리딩지저스 성경읽기

> 2026 그리스도 중심 성경 통독표와 기도노트. 모바일에서 읽고 체크하는 1인·본교회용 정적 웹 앱입니다.

[![Repository](https://img.shields.io/badge/GitHub-hanptceo%2Fbon--readingjesus-181717?logo=github)](https://github.com/hanptceo/bon-readingjesus)

**프로덕션:** [https://bon-readingjesus.vercel.app](https://bon-readingjesus.vercel.app)

---

## 한 줄 정의

**고정 일정 통독표** 또는 **시작일 맞춤 통독표**에서 매일의 읽기 분량을 확인하고, 탭 한 번으로 완료를 기록합니다. 기도노트는 월별로 제목·응답을 남깁니다.

---

## 화면 구성

| 파일 | URL (예) | 설명 |
|------|----------|------|
| `index.html` | `/` | **2026 고정 일정** 통독표 — 월별 탭, 오늘의 말씀 카드, 진행률, YouTube 영상 링크 |
| `prayer-note.html` | `/prayer-note.html` | `index.html`용 **기도노트** — 달력 1~12월 |
| `v2.html` | `/v2.html` | **시작일 맞춤** 통독표 — 사용자가 읽기 시작일을 등록 |
| `prayer-note2.html` | `/prayer-note2.html` | `v2.html`용 **기도노트** — 통독 시작월에 맞춘 월 탭 |
| `bible-app-icon.png` | — | favicon · apple-touch-icon |

### 어떤 통독표를 쓸까?

| | `index.html` | `v2.html` |
|--|--------------|-----------|
| 일정 | 2026년 달력 고정 | 시작일부터 순서대로 배정 |
| 기도노트 | `prayer-note.html` | `prayer-note2.html` |
| 적합한 경우 | 교회 공통 일정 그대로 따를 때 | 개인 시작 시점이 다를 때 |

---

## 주요 기능

### 통독표 (`index.html` · `v2.html`)

- **오늘의 말씀** 카드 — 당일 읽기 분량 바로 확인
- **월별 탭** — 완료한 달은 표시
- **진행률** — 올해(또는 전체) 완료 일수 / 전체 일수
- **일별 행** — 날짜 탭으로 읽기 완료 체크 (완료 시각 저장)
- **▶ 영상** — 해당 날 YouTube 강의 링크
- **일/토** — 주말 행 색 구분
- **초기화** — 체크 기록 삭제 (`v2`는 시작일 포함)

### 기도노트 (`prayer-note.html` · `prayer-note2.html`)

- 월별 **기도 제목** 추가·수정·삭제
- **응답 시기·내용** 기록
- **응답목록** — 응답된 기도만 모아 보기
- 통독표로 바로 이동

---

## 기술 스택

| 영역 | 기술 |
|------|------|
| 앱 | 정적 HTML + CSS + Vanilla JS |
| 빌드 | 없음 (별도 `npm install` 불필요) |
| 데이터 | 브라우저 `localStorage` (기기별) |
| 폰트 | [Noto Sans KR](https://fonts.google.com/noto/specimen/Noto+Sans+KR) |
| 배포 | [Vercel](https://bon-readingjesus.vercel.app) |
| 소스 | GitHub `main` → 자동 배포 |

### 디자인

- 배경 `#F5F5F4`, 포인트 `#F97316` (오렌지)
- 모바일 우선, 최대 너비 640px
- [bon-readingjesus.vercel.app](https://bon-readingjesus.vercel.app) 스타일 기준

---

## 로컬에서 확인

```bash
git clone https://github.com/hanptceo/bon-readingjesus.git
cd bon-readingjesus
```

브라우저에서 `index.html`을 직접 열거나, 정적 서버로 띄웁니다.

```bash
# Python 3
python -m http.server 8080

# Node (npx)
npx serve .
```

[http://localhost:8080/index.html](http://localhost:8080/index.html) 접속 후, DevTools 기기 모드로 모바일 UI를 확인합니다.

---

## 데이터 저장 (localStorage)

서버·계정 없이 **이 기기·이 브라우저**에만 저장됩니다. 기기를 바꾸면 데이터가 이어지지 않습니다.

| 키 | 사용 파일 | 내용 |
|----|-----------|------|
| `bible2026_checks` | `index.html` | 읽기 완료 (`월-일` → 완료 시각) |
| `prayer2026_notes` | `prayer-note.html` | 월별(0~11) 기도 배열 |
| `bibleReading_flex` | `v2.html` | `startDate`, `checks`, `monthKeys` |
| `prayer_flex_notes` | `prayer-note2.html` | 시작일 기준 월 키별 기도 배열 |

`index` 계열과 `v2` 계열의 저장소는 **서로 분리**됩니다.

---

## 배포

1. `main` 브랜치에 push
2. Vercel이 `index.html`을 루트로 자동 배포

| 항목 | 값 |
|------|-----|
| 브랜치 | `main` |
| 저장소 | [github.com/hanptceo/bon-readingjesus](https://github.com/hanptceo/bon-readingjesus) |
| URL | [bon-readingjesus.vercel.app](https://bon-readingjesus.vercel.app) |

---

## 프로젝트 구조

```
bon-readingjesus/
├── index.html          # 2026 고정 통독표
├── prayer-note.html    # 고정 일정용 기도노트
├── v2.html             # 시작일 맞춤 통독표
├── prayer-note2.html   # 시작일 맞춤 기도노트
├── bible-app-icon.png
├── README.md
└── WORKLOG.md          # 작업 이력 (개발용)
```

---

## 로드맵 (참고)

- [ ] `index.html`과 `v2.html` 통합 여부 결정
- [ ] Supabase 등 클라우드 동기화 (현재 범위 밖)
- [ ] PWA / 홈 화면 추가 (선택)

---

## 관련 문서

- [WORKLOG.md](./WORKLOG.md) — 작업 이력·맥락 메모

---

*Last updated 2026.06.22*
