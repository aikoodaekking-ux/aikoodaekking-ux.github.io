# 클릭존 배포 및 등록 가이드

## 0. 배포 전 꼭 바꿔야 할 것
- [x] 문의 이메일: `aikoodaekking@gmail.com` 으로 교체 완료 (`contact.html`, `en/contact.html`)
- [ ] `sitemap.xml`, `robots.txt`의 `https://YOUR-DOMAIN-HERE`를 실제 배포 주소로 교체 (1단계에서 주소가 정해진 뒤 진행)
- [ ] 광고 자리(`<div class="ad-slot">...</div>`, 게임 파일의 `#ad-top`/`#ad-bottom`)는 애드센스 심사 통과 후 `<ins class="adsbygoogle">` 코드로 교체

---

## 1. GitHub Pages로 배포하기

1. https://github.com 에서 새 저장소(Repository) 생성
   - 이름 예: `clickzone` (Public으로 생성해야 무료 Pages 사용 가능)
2. 로컬 프로젝트를 저장소에 연결하고 푸시
   ```
   git remote add origin https://github.com/<본인계정>/clickzone.git
   git branch -M main
   git push -u origin main
   ```
3. GitHub 저장소 페이지 → **Settings → Pages**
   - Source: `Deploy from a branch`
   - Branch: `main` / `/ (root)` 선택 → Save
4. 몇 분 후 `https://<본인계정>.github.io/clickzone/` 주소로 접속 가능
5. (선택) 커스텀 도메인이 있다면 같은 Pages 설정 화면에서 Custom domain 입력 후, 도메인 등록업체에서 CNAME/A 레코드를 GitHub Pages로 연결

> 주의: 저장소 경로가 `/clickzone/`처럼 하위 폴더가 되므로, 이 프로젝트의 모든 링크는 절대경로(`/`)가 아닌 상대경로(`./`, `../`)로 작성되어 있어 하위 폴더 배포에도 그대로 동작합니다.

배포 주소가 정해지면 `sitemap.xml`과 `robots.txt`의 `YOUR-DOMAIN-HERE`를 실제 주소로 바꾸고 다시 커밋·푸시하세요.

---

## 2. Google Search Console 등록

1. https://search.google.com/search-console 접속 후 Google 계정으로 로그인
2. "URL 접두어" 방식으로 사이트 주소 입력 (예: `https://내계정.github.io/clickzone/`)
3. 소유권 확인: "HTML 태그" 방식을 추천
   - Search Console이 알려주는 `<meta name="google-site-verification" content="...">` 태그를 모든 `index.html`(최소 루트 index.html)의 `<head>`에 추가
   - 저장 후 다시 커밋/푸시 → Search Console에서 "확인" 클릭
4. 확인 완료 후, 왼쪽 메뉴 **Sitemaps** → `sitemap.xml` 제출
5. 며칠~몇 주 내로 색인(검색 노출) 반영 시작. **색인 생성** 메뉴에서 URL 검사도 가능

---

## 3. 네이버 서치어드바이저 등록

1. https://searchadvisor.naver.com 접속 후 네이버 계정 로그인
2. "사이트 등록" → 사이트 주소 입력
3. 소유권 확인: "HTML 태그" 또는 "HTML 파일 업로드" 중 선택
   - HTML 태그 방식이면 Search Console과 동일하게 `<head>`에 태그 추가 후 재배포
4. 등록 완료 후 좌측 메뉴 **요청 → 사이트맵 제출**에서 `sitemap.xml` 제출
5. **요청 → 웹 페이지 수집** 메뉴에서 주요 페이지(홈, 게임 페이지) 수집 요청을 하면 반영이 더 빨라집니다

---

## 4. Google AdSense 신청 및 광고 삽입

### 신청 전 체크리스트 (반려를 피하기 위해)
- [ ] 콘텐츠 페이지가 충분한가 (이 사이트는 블로그 10개 + 게임 페이지 + 소개/문의/정책 페이지로 구성되어 있음)
- [ ] 개인정보처리방침(`privacy.html`) / 이용약관(`terms.html`) 페이지가 있는가 → 이미 포함됨
- [x] 실제 연락 가능한 이메일이 `contact.html`에 있는가 → `aikoodaekking@gmail.com`으로 교체 완료
- [ ] 사이트가 실제 도메인(또는 github.io 주소)으로 몇 주 이상 운영되어 콘텐츠가 쌓였는가 (신규 사이트는 보류될 수 있음)

### 신청 절차
1. https://www.google.com/adsense 접속 → 사이트 주소 입력 후 가입 신청
2. 발급된 코드(`<script async src="https://pagead2.googlesyndication.com/...">`)를 **모든 페이지의 `<head>` 맨 위**에 추가
   - 이 프로젝트는 페이지가 많으므로, 번거롭다면 우선 홈/게임 페이지에만 넣고 심사 통과 후 나머지 페이지에 확장해도 됩니다
3. 심사는 보통 수일~수주 소요됩니다. 심사 중에는 "ads.txt 필요" 안내가 뜨면 루트에 `ads.txt` 파일을 추가하라는 의미이니, 애드센스가 알려주는 내용을 그대로 `ads.txt` 파일로 루트에 추가하세요
4. 승인 후, 애드센스 대시보드에서 "광고 단위" 생성 → 각 단위의 `<ins class="adsbygoogle" ...></ins>` 코드를 받아서
   - 사이트의 `<div class="ad-slot">광고 영역 (AD)</div>` 부분을 해당 코드로 교체
   - 게임 파일(`games/reflex-clicker.html`)의 `#ad-top`, `#ad-bottom` 안의 텍스트도 동일하게 교체
5. 애드센스 정책상 "본인 광고 클릭 금지", "클릭 유도 문구 금지"를 반드시 지켜주세요.

---

## 5. 운영 팁
- 블로그 글을 꾸준히(월 1~2개씩) 추가하면 검색 유입과 애드센스 심사에 모두 긍정적입니다. 새 글을 추가할 때마다 `sitemap.xml`에도 URL을 추가해주세요.
- 게임을 추가로 만들면 `games/` 폴더에 새 HTML 파일을 추가하고, `games/index.html`과 홈 화면에 카드를 추가하는 구조를 그대로 재사용하면 됩니다.
