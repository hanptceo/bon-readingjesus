# 작업 로그 (WORKLOG)

PC·장소가 바뀌어도 Cursor Agent가 맥락을 잡을 수 있도록, **짧게·자주** 기록합니다.

---

## 프로젝트 요약

| 항목 | 내용 |
|------|------|
| 앱 | 2026 성경읽기 통독표 · 기도노트 (1인·본교회용) |
| 스택 | 정적 HTML + CSS + Vanilla JS (빌드 없음) |
| 데이터 | **localStorage** (기기·브라우저별, 서버 없음) |
| 디자인 | 오프화이트 배경 `#F5F5F4`, 오렌지 포인트 `#F97316`, Noto Sans KR, 모바일 우선 |
| 경로 | `C:\dev\vibecoding\bon-readingjesus` |
| Git | `main` → https://github.com/hanptceo/bon-readingjesus |
| 배포 | Vercel **https://bon-readingjesus.vercel.app** |

### 주요 파일·화면

| 파일 | 설명 |
|------|------|
| `index.html` | **2026 고정 일정** 통독표 — 월별 탭, 오늘 카드, 진행률, YouTube 영상 |
| `prayer-note.html` | `index.html`용 **기도노트** — 달력 1~12월 |
| `v2.html` | **시작일 맞춤** 통독표 — 사용자 등록 시작일 기준 일정 |
| `prayer-note2.html` | `v2.html`용 **기도노트** — 통독 `monthKeys`에 맞춘 월 탭 |
| `bible-app-icon.png` | favicon · apple-touch-icon |
| `README.md` | 프로젝트 소개·실행·배포 문서 |

### localStorage 키

| 키 | 용도 |
|----|------|
| `bible2026_checks` | `index.html` 읽기 완료 (`월-일` → 완료 시각) |
| `prayer2026_notes` | `prayer-note.html` 월별(0~11) 기도 배열 |
| `bibleReading_flex` | `v2.html` — `startDate`, `checks`, `monthKeys` |
| `prayer_flex_notes` | `prayer-note2.html` — 월 키별 기도 배열 |

### 알려진 미완

- [ ] `index.html`과 `v2.html` 통합 여부 결정
- [ ] Supabase 등 클라우드 동기화 (현재 범위 밖)
- [ ] PWA / 홈 화면 추가 (선택)

---

## 현재 상태 (한 줄)

**2026-06-22** — `prayer-note2`, UI 조정, README·WORKLOG 정리. 커밋 `97908e6` push 완료 예정.

**브랜치:** `main` (`origin/main`)

**다음:**

1. (선택) `index` / `v2` 통합 여부 결정
2. Vercel 프로덕션에서 `v2.html`·`prayer-note2.html` 동작 확인

---

## 환경 메모

| PC | 경로 | 비고 |
|----|------|------|
| office | `C:\dev\vibecoding\bon-readingjesus` | 2026-06-22 UI·문서·v2 기도노트 |

- 로컬 확인: `index.html` 직접 열기 또는 `python -m http.server`
- 배포: `git push origin main` → Vercel 자동 배포
- 데이터는 **기기 localStorage** — 브라우저·기기마다 분리

---

## 로그 (최신이 위)

### 2026-06-22 — v2 기도노트·UI·문서

**한 일**

- `prayer-note2.html` — `v2.html` 시작일·`monthKeys` 기준 월별 기도노트
- `v2.html` — 기도노트 링크, `monthKeys` 저장, `initFromStore()` 복원 버그 수정
- `index.html`·`v2.html` — 일별 행 높이 축소(~18%), 본문 폰트 +1px, 오늘 카드 타이틀 16px
- 전체 HTML footer — `Last updated 2026.06.22`
- `README.md` 작성, `WORKLOG.md` 정리

**Git:** `97908e6`

---

### 2026-06-21 — 기도노트·favicon·UI 개선

**한 일**

- `prayer-note.html` 추가 — 월별 기도 제목, 응답 시기·내용 기록
- `index.html` 헤더 **기도노트** 링크, favicon
- 오늘 카드·진행률·월별 탭 UI 개선

**Git:** `bc08a14`, `98d66ec`

---

### 2026-06-15 ~ 2026-06-17 — 통독표 초기 구축

**한 일**

- `index.html` — 2026 월별 읽기 일정, 체크·진행률, YouTube 영상
- `v2.html` — 시작일 설정형 유연 일정
- GitHub 업로드

**Git:** `8b432f2` ~ `89f6d34`

---

## 이후 작업 템플릿

```markdown
### YYYY-MM-DD — (한 줄 제목)

**한 일**
- 

**Git:** (커밋 해시)

**다음**
- 
```
