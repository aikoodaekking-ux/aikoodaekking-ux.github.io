# 클릭존 배포 및 등록 가이드

## 배포 완료 정보
- **GitHub 저장소**: https://github.com/aikoodaekking-ux/aikoodaekking-ux.github.io
- **라이브 사이트**: https://aikoodaekking-ux.github.io/
- **GitHub 계정**: aikoodaekking-ux
- **문의 이메일**: aikoodaekking@gmail.com

> 처음에는 `clickzone` 프로젝트 저장소로 배포했으나(`.../clickzone/` 경로), 네이버 서치어드바이저가 "호스트 단위" 주소만 등록 가능해서 저장소를 `aikoodaekking-ux.github.io`로 이름을 바꿔 **루트 주소**로 마이그레이션했습니다.

## 0. 배포 전 꼭 바꿔야 할 것
- [x] 문의 이메일: `aikoodaekking@gmail.com` 으로 교체 완료 (`contact.html`, `en/contact.html`)
- [x] `sitemap.xml`, `robots.txt`를 실제 배포 주소(`https://aikoodaekking-ux.github.io`)로 교체 완료
- [x] Google Search Console 소유권 확인 태그 반영 완료 (`index.html`)
- [ ] 광고 자리(`<div class="ad-slot">...</div>`, 게임 파일의 `#ad-top`/`#ad-bottom`)는 애드센스 심사 통과 후 `<ins class="adsbygoogle">` 코드로 교체

---

## 1. GitHub Pages 배포 (완료됨 ✅)

저장소 생성, 코드 푸시, Pages 활성화, 루트 주소 마이그레이션까지 모두 완료되었습니다.
- https://aikoodaekking-ux.github.io/ 에서 바로 접속 가능합니다.
- 앞으로 파일을 수정하면 아래 명령으로 다시 배포됩니다:
  ```
  git add -A
  git commit -m "변경 내용"
  git push
  ```
  푸시 후 1~2분 내 자동으로 사이트에 반영됩니다.
- (선택) 커스텀 도메인을 쓰고 싶다면 저장소 **Settings → Pages**에서 Custom domain을 입력하고, 도메인 등록업체에서 CNAME/A 레코드를 GitHub Pages로 연결하세요. 이 경우 `sitemap.xml`/`robots.txt`의 도메인도 다시 교체해야 합니다.

> 참고: 이 프로젝트의 모든 내부 링크는 절대경로(`/`)가 아닌 상대경로(`./`, `../`)로 작성되어 있어서, 루트 배포든 하위 폴더 배포든 구조 변경 없이 그대로 동작합니다.

---

## 2. Google Search Console 등록

1. https://search.google.com/search-console 접속 후 Google 계정으로 로그인
2. 기존에 `.../clickzone/` 주소로 등록했다면 주소가 바뀌었으니 **새 속성**을 "URL 접두어" 방식으로 추가: `https://aikoodaekking-ux.github.io/`
3. 소유권 확인: "HTML 태그" 방식 — `index.html`에 이미 인증 태그가 반영되어 있으니 동일 토큰이면 바로 "확인" 클릭. 새 토큰이 발급되면 알려주시면 제가 반영하겠습니다.
4. 확인 완료 후, 왼쪽 메뉴 **Sitemaps** → `sitemap.xml` 제출 (`https://aikoodaekking-ux.github.io/sitemap.xml`)
5. 며칠~몇 주 내로 색인(검색 노출) 반영 시작. **색인 생성** 메뉴에서 URL 검사도 가능

---

## 3. 네이버 서치어드바이저 등록

> 처음에 `.../clickzone/` 주소로 등록을 시도하면 "URL을 호스트 단위로 입력해주세요" 오류가 납니다. 네이버는 경로(path) 없는 호스트 루트 주소만 등록을 받기 때문입니다. 이 문제를 해결하려고 사이트를 루트 주소(`https://aikoodaekking-ux.github.io/`)로 마이그레이션했으니, 아래처럼 새 주소로 다시 등록해주세요.

1. https://searchadvisor.naver.com 접속 후 네이버 계정 로그인
2. "사이트 등록" → 사이트 주소에 정확히 `https://aikoodaekking-ux.github.io` 입력 (끝에 `/clickzone` 등 경로를 붙이지 않기)
3. 소유권 확인: "HTML 태그" 또는 "HTML 파일 업로드" 중 선택
   - HTML 태그 방식이면 나오는 메타 태그를 저한테 보내주세요, 바로 반영해드릴게요
   - HTML 파일 업로드 방식이면 받은 파일을 저한테 전달해주시면 저장소 루트에 추가해드릴게요
4. 등록 완료 후 좌측 메뉴 **요청 → 사이트맵 제출**에서 `https://aikoodaekking-ux.github.io/sitemap.xml` 제출
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
