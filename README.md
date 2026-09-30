# 분당 당근 ROCK 페스티벌 - Vercel 배포용

이 폴더는 별도 빌드 없이 Vercel에 바로 배포할 수 있는 정적 웹사이트입니다.

## 파일 구성

- `index.html` : 모바일 웹앱 본체
- `vercel.json` : Vercel 정적 배포 설정

## 가장 쉬운 배포 방법 — Vercel 웹에서 업로드

1. https://vercel.com 에 로그인합니다.
2. Dashboard에서 **Add New → Project** 를 선택합니다.
3. 이 폴더를 GitHub 저장소에 올린 뒤 저장소를 Import하거나,
   Vercel의 파일/폴더 업로드 기능을 사용할 수 있는 화면에서는 이 폴더를 업로드합니다.
4. Framework Preset은 별도로 지정할 필요가 없습니다. 정적 HTML 사이트로 인식됩니다.
5. Build Command / Output Directory / Install Command는 모두 비워둬도 됩니다.
6. **Deploy**를 누릅니다.
7. 배포가 끝나면 `https://프로젝트명.vercel.app` 형태의 주소가 생깁니다.

## Vercel CLI로 배포

Node.js가 설치되어 있다면:

```bash
npm install -g vercel
cd bundang-carrot-rock-vercel
vercel
```

처음 질문에는 다음처럼 답하면 됩니다.

- Set up and deploy? → `Y`
- Which scope? → 본인 계정 선택
- Link to existing project? → 처음이면 `N`
- Project name? → 원하는 이름
- In which directory is your code located? → `./`
- Want to modify settings? → `N`

운영 배포는:

```bash
vercel --prod
```

## 현재 버전에서 꼭 알아둘 점

현재 기대평/응원, 리액션, Open Mic 신청/투표 데이터는 브라우저의 `localStorage`에 저장됩니다.
따라서 **한 휴대폰에서 쓴 내용이 다른 관객의 휴대폰에는 공유되지 않습니다.**

즉, 현재 파일은 디자인/현장 동선 확인과 단일 기기 데모에는 그대로 사용할 수 있지만,
실제 공연장에서 여러 사람이 같은 방명록과 투표 결과를 공유하려면 Supabase/Firebase 같은
공용 데이터베이스를 다음 단계에서 연결해야 합니다.

YouTube 영상은 각 곡 상세 화면에서 `youtube.com/embed` 방식으로 재생됩니다.
일부 영상은 업로더의 임베드 정책에 따라 재생이 제한될 수 있습니다.
