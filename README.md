# AWS SAA 기초 개념 핸드북

AWS Certified Solutions Architect – Associate(SAA) 시험의 기초 용어·서비스를 **링크·체크·필터·검색**으로 학습하는 오프라인 가능한 PWA입니다.

**🔗 배포 주소: https://aws-saa-study.vercel.app**

아이폰/안드로이드 브라우저에서 위 주소를 열고 홈 화면에 추가하면 앱처럼 사용할 수 있습니다.

## 주요 기능

- **10개 카테고리 학습** — 클라우드/아키텍처, 보안/IAM, 네트워크/CDN/DNS, 컴퓨팅/컨테이너, 스토리지, 데이터베이스/캐시, 서버리스/통합, 운영/모니터링/IaC/비용, 마이그레이션/분석 등
- **체크·필터·검색** — 학습한 개념을 체크하고, 미학습 항목만 필터링하거나 키워드로 검색
- **진행 상태 저장** — 체크 상태는 브라우저 `localStorage`에 자동 저장 (서버 저장 아님)
- **백업/불러오기** — JSON으로 진행 상태를 내보내고 다른 기기에서 불러오기
- **오프라인 지원 (PWA)** — Service Worker 캐시로 네트워크 없이도 열람 가능
- **홈 화면 설치** — iOS/Android에서 앱 아이콘으로 설치

## 홈 화면에 앱으로 설치하기 (iPhone)

1. iPhone Chrome/Safari에서 https://aws-saa-study.vercel.app 접속
2. 공유 버튼 → **홈 화면에 추가**
3. 홈 화면 아이콘으로 실행하면 앱처럼 전체 화면으로 사용

> 체크 상태는 같은 브라우저·같은 URL 기준으로 유지됩니다. 브라우저 데이터 삭제·시크릿 모드·다른 기기에서는 별도 관리되니, 기기를 옮길 때는 **백업(JSON 내보내기) → 불러오기**를 사용하세요.

## 파일 구성

| 파일 | 설명 |
|---|---|
| `index.html` | 학습형 핸드북 (단일 파일, 의존성 없음) |
| `manifest.webmanifest` | PWA 앱 정보 (이름·아이콘·테마) |
| `sw.js` | 오프라인 캐시용 Service Worker |
| `icon-*.png` | 홈 화면 아이콘 (192/512/maskable) |
| `vercel.json` | Vercel 배포 설정 (PWA용 캐시·헤더) |

## 배포 (Vercel)

이 저장소는 Vercel에 연결되어 있어 `main` 브랜치에 push하면 자동 배포됩니다.

```bash
# 변경 후 push → 자동 배포
git push origin main

# 또는 CLI로 즉시 프로덕션 배포
vercel --prod
```

빌드 과정이 없는 순수 정적 사이트이며, `vercel.json`에서 다음을 처리합니다.

- `sw.js`·`index.html`: 캐시 안 함(`must-revalidate`) → 수정 시 즉시 반영
- `manifest.webmanifest`: 올바른 Content-Type 지정
- 아이콘 PNG: 1주일 캐시

## 로컬에서 실행

정적 파일이므로 아무 정적 서버로 열면 됩니다.

```bash
npx serve .
# 또는
python3 -m http.server 3000
```

> `file://`로 직접 열면 체크/필터/localStorage는 되지만, iOS에서 PWA 설치와 Service Worker 오프라인 캐시는 HTTPS 호스팅에서만 안정적으로 동작합니다.
