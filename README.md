# BoxCat

BoxCat 의 **출시 예정 앱 소개 및 고객 문의** 사이트입니다.

📧 boxcathq@gmail.com

---

## 로컬에서 확인하기

별도 빌드 과정 없는 정적 사이트입니다. `index.html` 을 브라우저로 바로 열면 됩니다.

또는 간단한 로컬 서버를 띄우려면:

```bash
# Python 이 설치되어 있다면
python -m http.server 8000
```

브라우저에서 http://localhost:8000 접속.

---

## GitHub Pages 배포 방법

### 1) 깃 저장소 만들기

```bash
git init
git add .
git commit -m "Initial commit: BoxCat website"
git branch -M main
```

### 2) GitHub 에 새 저장소 생성

- GitHub 에 로그인 → 우상단 `+` → **New repository**
- 저장소 이름은 자유롭게 (예: `boxcat-site`)
- **Public** 으로 생성 (무료 GitHub Pages 사용 시 필수)
- README 등 체크박스는 모두 해제 후 생성

### 3) 원격 저장소에 푸시

```bash
git remote add origin https://github.com/<본인계정>/<저장소이름>.git
git push -u origin main
```

### 4) GitHub Pages 활성화

1. 저장소 페이지 → **Settings** → 왼쪽 메뉴 **Pages**
2. **Source** 를 `Deploy from a branch` 로 설정
3. **Branch** 를 `main` / `/ (root)` 로 선택 후 **Save**
4. 잠시 후 상단에 `Your site is live at https://<본인계정>.github.io/<저장소이름>/` 표시됨

> 💡 저장소 이름을 `<본인계정>.github.io` 로 만들면 루트 도메인 (`https://<본인계정>.github.io`) 으로 바로 접속 가능합니다.

---

## 커스텀 도메인 연결 (선택사항)

도메인을 구매했다면 (예: `boxcat.co.kr`):

1. 저장소에 `CNAME` 파일 추가 (내용은 `boxcat.co.kr` 한 줄)
2. 도메인 등록 업체 DNS 설정에서 GitHub Pages 의 A 레코드 또는 CNAME 추가
   - A 레코드: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - 또는 CNAME: `<본인계정>.github.io`
3. Settings → Pages → **Custom domain** 에 도메인 입력
4. **Enforce HTTPS** 체크

---

## 파일 구조

```
.
├── index.html      # 메인 페이지
├── styles.css      # 스타일
├── script.js       # 간단한 스크립트 (footer 연도 등)
├── .nojekyll       # GitHub Pages 가 Jekyll 처리를 건너뛰도록
└── README.md
```

---

## 콘텐츠 수정 가이드

### 앱 카드 수정 (`index.html` 의 `<section id="apps">`)

각 앱 카드의 구조:

```html
<article class="app-card">
  <div class="app-thumb" style="background: linear-gradient(135deg, #ff7a3d, #ffb37a);">
    <span class="app-emoji" aria-hidden="true">📦</span>
  </div>
  <div class="app-body">
    <div class="app-meta">
      <span class="badge badge-dev">개발 중</span>
      <span class="app-platform">iOS · Android</span>
    </div>
    <h3>앱 이름</h3>
    <p>앱 소개 한두 문장.</p>
  </div>
</article>
```

- **앱 이름** 과 **소개 문구** 를 실제 앱 정보로 교체
- **이모지** 를 앱 컨셉에 맞게 변경 (예: 🎨 🎵 📚 🛒 ⏰)
- **그라데이션 색상** 을 앱 분위기에 맞게 수정
- **상태 배지** 종류:
  - `badge-plan` — 기획 중 (초록)
  - `badge-dev` — 개발 중 (오렌지)
  - `badge-soon` — 출시 예정 (파랑)
  - `badge-live` — 출시 완료 (초록 강조)
- **플랫폼** 표기: `iOS · Android`, `Web`, `Mobile Game` 등 자유롭게
- 앱을 추가하려면 `<article class="app-card">...</article>` 블록을 통째로 복사
- 실제 앱 스크린샷이 있다면 `<div class="app-thumb">` 안에 `<img src="..." />` 로 교체 가능

### 기타

- **소개 문구**: `<section id="about">` 영역
- **이메일 변경**: `index.html` 내 `mailto:boxcathq@gmail.com` 검색 후 수정
- **색상 변경**: `styles.css` 상단 `:root` 의 `--accent` 값 수정
