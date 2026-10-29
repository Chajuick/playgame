# PLAYDATE

둘이 하기 좋은 PC 온라인 협동 게임 추천 페이지.

`index.html` 하나로 동작하는 정적 사이트입니다. 브라우저에서 바로 열면 됩니다.
게임 이미지와 웹폰트는 인터넷 연결 시 불러옵니다.

## 기능
- 에디터 추천 배너, 에디터 픽, 2인 3만 원 이하 모음, 추천 랭킹
- 장르 · 그래픽 · 2인 예산 · 최대 인원 필터와 정렬, 검색
- 게임 상세(스크린샷, 가격, 협동 인원, 플레이어 반응)
- 찜 목록(브라우저 저장), 목록 복사 공유, 랜덤 고르기
- 라이트 / 다크 테마

## 데이터 기준
- 가격: 2026-10-28 SteamDB 한국 원화(세일가 포함), 2인 가격은 각자 1개씩 구매 가정
- 최대 인원: PC 온라인 협동 기준, 업데이트에 따라 달라질 수 있음
- 플레이타임과 점수: 편집자의 주관적 추정

## PWA · 공유 · 검색 설정
- `manifest.webmanifest`, `sw.js`: 홈 화면 설치, 오프라인 열람(한 번 방문한 뒤)
- `og-image.png`: 카카오톡 · 디스코드 · X 등 링크 미리보기 이미지(1200×630)
- `robots.txt`, `sitemap.xml`, JSON-LD 구조화 데이터
- 배포 주소는 `https://playgame-peach.vercel.app/` 기준. 주소가 바뀌면 `index.html`의 canonical · og:url · og:image, `robots.txt`, `sitemap.xml`을 함께 고칩니다.
- `index.html`이나 아이콘을 바꾼 뒤에는 `sw.js`의 `VERSION`을 올려야 설치된 앱에도 반영됩니다.

## PC 런처 (`launcher/`)
- `launcher/index.html`: PC 런처 소개 · 설치 안내 · 업데이트 내역 페이지
- `launcher/PCLauncher-Setup.exe`, `launcher/latest.json`: 최신 설치 파일과 버전 정보. 직접 고치지 말고 `pc-launcher` 저장소에서 `npm run release -- <버전> "바뀐 점"`으로 만듭니다.
- 설치된 런처는 `latest.json`을 6시간마다 읽어 새 버전을 알리고, SHA-256이 맞는 설치 파일만 실행합니다.
- `vercel.json`: 두 파일이 캐시되지 않도록 헤더를 지정합니다. `sw.js`도 이 두 파일은 캐시하지 않습니다.
