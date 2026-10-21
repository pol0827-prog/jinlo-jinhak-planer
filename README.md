# 진로진학 합격노트

진로진학상담교사 임용 준비 · 경기도교육청 선발 대비 개인 학습 앱

- 자료실 → 텍스트 변환 → AI 정제 → 구조화 맵 → 학습지, 1·3·7·14·30일 복습
- 알림판, 빈 노트, 휴지통
- 온라인 모의면접(인성 → 즉답형 → 구상형, 녹화, Gemini 루브릭 채점), 문항 관리, 연습 기록
- 정량평가(산출표, 연도별 점수와 2027~2030 예상 점수)

## 구성

| 파일 | 내용 |
| --- | --- |
| `index.html` | 앱 전체 (Firebase SDK 13.0.0 내장) |
| `firestore.rules` | Firestore 보안 규칙: 허용된 두 구글 계정만 `spaces/hapgyeok` 읽기·쓰기 |
| `firebase.json`, `firestore.indexes.json` | Firebase CLI 배포용 설정 |

## 저장 방식

- 로그인(구글): `firestore.rules`에 적은 계정만 들어올 수 있고, 그 계정들은 같은 자료를 봄
- Firestore(Spark 무료 요금제): 텍스트·정제본·맵·학습지·노트·알림판·문항·면접 결과·정량평가·설정
- 각 컴퓨터의 브라우저(IndexedDB): 자료 원본 파일, 면접 녹화 영상(내 컴퓨터에 저장)
- Gemini API 키: 설정에 넣으면 Firestore의 내 공간에 함께 저장됨

## 배포 (Vercel)

1. 이 저장소를 Vercel에 가져오기(Framework: Other, 빌드 명령 없음)
2. 배포된 주소(예: `hapgyeok-note.vercel.app`)를 Firebase 콘솔 → Authentication → 설정 → **승인된 도메인**에 추가
3. 배포 주소로 열고 구글 계정으로 로그인

`index.html`을 파일로 바로 열면 로그인 없이 그 컴퓨터에만 저장돼요.
