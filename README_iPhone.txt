AWS SAA 핸드북 PWA 패키지

구성
- index.html: 학습형 핸드북
- manifest.webmanifest: 홈 화면 앱 정보
- sw.js: 오프라인 캐시용 Service Worker
- icon-*.png: 홈 화면 아이콘

아이폰 Chrome에서 앱처럼 쓰는 방법
1. 이 폴더의 파일을 정적 호스팅에 올립니다. 예: Vercel, Netlify, GitHub Pages, 사내 정적 서버.
2. iPhone Chrome에서 해당 HTTPS URL을 엽니다.
3. 주소창 오른쪽 공유 버튼을 누릅니다.
4. Add to Home Screen / 홈 화면에 추가를 선택합니다.
5. 이후 홈 화면 아이콘으로 실행하면 앱처럼 사용할 수 있습니다.

주의
- file:// 로컬 파일로 열면 체크/필터/localStorage는 사용할 수 있지만, iOS에서 완전한 PWA 설치와 Service Worker 오프라인 캐시는 안정적으로 동작하지 않을 수 있습니다.
- 체크 상태는 서버에 저장되지 않습니다. 같은 브라우저/같은 URL의 localStorage에 저장됩니다.
- 다른 기기로 옮길 때는 백업 버튼으로 JSON을 내보낸 뒤 불러오기를 사용하세요.
