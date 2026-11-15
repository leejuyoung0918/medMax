# MED-MAX · 약꾹

장기 복약자가 공동체 공간에서 서로 지지하고 약사에게 비동기로 질문할 수 있도록 만든 2024년 가을 Tech for Impact 팀 프로젝트입니다. Unity WebGL 공간을 React Native 앱의 WebView에 연결합니다.

[프로젝트 사례와 개인 역할](https://leejuyoung0918.github.io/med-max.html) · [팀 소개·데모·기존 상세 기록](docs/PROJECT_STORY.md)

## 어떤 문제를 해결하려 했나

복약 기록만 보여주는 화면에서 더 나아가, 사용자들이 같은 공간과 공동 목표를 공유하는 경험을 구현했습니다. 약사가 계속 접속해 있어야 하는 부담을 고려해 Q&A는 비동기 구조로 구성했습니다. 실제 복약 순응도 개선은 측정 결과가 아닌 프로젝트의 목표입니다.

## 본인 역할과 팀 결과

기존 포트폴리오에 기록된 이주영의 담당은 Unity 클라이언트와 UI의 로그인·입력 검증·화면 전환, WebSocket을 통한 위치·이동 상태 동기화, HTTP 사용자·복약 정보 연결입니다. React Native·서버·AI를 포함한 전체 시스템은 팀 공동 결과입니다.

팀은 Unity 공간과 React Native 앱을 연결하고 방 ID를 기준으로 사용자를 같은 공간에 배정했습니다. 기존 포트폴리오에는 팀의 Tech for Impact 사회가치상 수상 이력이 기록되어 있습니다. 이 저장소는 사용자 복약 지속 효과에 대한 별도 실험 결과를 제공하지 않습니다.

## 기술 선택과 학습

- **Unity WebGL + WebView**: 게임 공간을 기존 모바일 화면 안에 연결하는 구조입니다. 앱 화면과 게임 상태, 로그인·방 식별자의 경계를 함께 맞춰야 합니다.
- **WebSocket + HTTP**: 실시간 위치 상태와 요청·응답형 사용자 정보를 서로 다른 통신 경로로 처리합니다. 연결 성공뿐 아니라 같은 사용자를 가리키는지와 화면 반영까지 확인해야 합니다.
- **TypeScript + React Native**: UI와 데이터 구조를 표현하는 기존 코드가 있습니다. `tsconfig.json` 존재만으로 API 입력 검증이나 엄격한 타입 검사가 완성되었다고 보지는 않습니다.

## 디렉터리

| 경로 | 역할 |
|---|---|
| [frontEnd](frontEnd) | React Native·TypeScript 모바일 UI |
| [Unity](Unity) | 커뮤니티 공간과 Unity 클라이언트 |
| [backEnd](backEnd) | Node.js 서비스·라우터와 DB 연동 |
| [AI](AI) | Q&A 관련 Python 구성요소 |

## 개발 시작

```bash
git clone https://github.com/leejuyoung0918/medMax.git
cd medMax/frontEnd
npm ci
npm start
```

별도 터미널에서 `npm run android` 또는 `npm run ios`를 실행합니다. Android Studio 또는 Xcode와 플랫폼별 개발 환경이 필요합니다. 실제 앱 실행에는 백엔드 주소·DB·Unity 산출물 등 팀 통합 환경이 필요합니다.

```bash
cd ../backEnd
npm ci
node app.js
```

서버 구성은 [백엔드 README](backEnd/README.md), 모바일 환경은 [프론트엔드 README](frontEnd/README.md), AI 실행은 [AI 디렉터리](AI)를 참고하세요. 저장소의 기존 lockfile을 사용하며 루트의 설치 결과를 각 앱의 의존성으로 간주하지 않습니다.

## 검증 상태와 개선 과제

이번 정리는 팀 소개 중심의 README를 문제·역할·결과·학습·재현 안내로 재구성한 문서 변경입니다. 기존 상세 기록은 별도 문서에 보존했습니다. 네이티브 빌드·통합 서버·실사용자 효과를 새로 검증한 변경은 아닙니다.

실제 TypeScript 역량을 더 명확히 보여주려면 API 응답의 런타임 검증, 엄격한 타입 검사, 비어 있는 데이터의 UI 테스트를 별도 변경으로 보강해야 합니다. 공통 개발 도구의 코드·CI·검증 경험은 [SBOM 저장소](https://github.com/leejuyoung0918/sbom-vulnerability-propagation)를 우선 참고하세요.
