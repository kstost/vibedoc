# VibeDOC 📝

[![npm version](https://badge.fury.io/js/vibedoc.svg)](https://badge.fury.io/js/vibedoc)
[![Node.js CI](https://github.com/username/vibedoc/workflows/Node.js%20CI/badge.svg)](https://github.com/username/vibedoc/actions)
[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL%203.0-blue.svg)](https://opensource.org/licenses/AGPL-3.0)

쉽게 PRD, TRD, TODO List를 만들 수 있는 vibe document 생성 도구

## 🎯 개요

VibeDOC은 코딩을 전혀 모르는 사람들을 위해 간단한 아이디어를 확장시켜 MVP 형태로 빠르게 만들어 볼 수 있도록 PRD, TRD 등의 형태로 기획을 만드는데 도움을 드리는 프로그램입니다.

사용자 설문을 통해 자동으로 완전한 개발 문서 세트를 생성하는 도구입니다:
- **PRD** (Product Requirements Document) - 제품요구사항문서
- **TRD** (Technical Requirements Document) - 기술요구사항문서  
- **TODO** - 개발 할일 목록

10개의 질문에 답하기만 하면 프로젝트에 필요한 모든 문서가 자동으로 생성됩니다.

## ✨ 주요 기능

### 📋 인터랙티브 설문 시스템
- 10개의 핵심 질문을 통해 프로젝트 요구사항 수집
- 다중 선택 또는 직접 입력 방식 지원
- 진행 상황 표시 (예: [3/10])

### 🤖 AI 기반 문서 생성
- OpenAI GPT를 활용한 고품질 문서 자동 생성
- 각 문서별 최적화된 프롬프트 시스템
- 구체적이고 실행 가능한 내용 생성

### 📄 3단계 문서 생성 파이프라인
1. **PRD 생성**: 설문 결과를 바탕으로 제품요구사항문서 생성
2. **TRD 생성**: PRD를 기반으로 기술요구사항문서 생성
3. **TODO 생성**: TRD를 기반으로 개발 할일 목록 생성

### ⚙️ 환경변수 기반 설정
- 모델별 세부 설정 가능 (GPT-5, GPT-4 등)
- Verbosity 및 Reasoning effort 조절
- 각 단계별 독립적 설정 지원

## 🚀 설치 및 실행

### 필수 요구사항
- OpenAI API Key (필수)

### 설치
```bash
npm i vibedoc -g
```



### 실행

```bash
vibedoc                    # 기본 실행 (10개 질문)
vibedoc --help             # 도움말 보기
vibedoc --version          # 버전 확인
vibedoc -v                 # 상세 출력 모드
vibedoc -q 5               # 질문 5개로 설정
vibedoc --questions 15     # 질문 15개로 설정
vibedoc --skip-trd         # TRD 생성 건너뛰기
vibedoc --skip-todo        # TODO 생성 건너뛰기
```

## 📖 사용법

### 1️⃣ API 키 설정
```bash
vibedoc config set apikey [your-openai-api-key]
```

### 2️⃣ 모델 설정 (선택사항)
```bash
# 전체 모델 설정
vibedoc config set model gpt-5

# 단계별 모델 설정
vibedoc config set prd-model gpt-5
vibedoc config set trd-model gpt-4
vibedoc config set todo-model gpt-4
```

### 3️⃣ 설정 확인
```bash
vibedoc config list
```

### 4️⃣ 문서 생성 시작
```bash
vibedoc
```

### 5️⃣ 질문 응답
시스템이 제시하는 10개의 질문에 순차적으로 답변합니다:
- 대상 사용자
- 핵심 기능
- 기술 스택 선호도
- 성능 요구사항
- 보안 요구사항
- 등등...

### 6️⃣ 문서 생성 대기
AI가 다음 순서로 문서를 자동 생성합니다:
1. PRD 문서 생성 → `prd.md` 저장
2. TRD 문서 생성 → `trd.md` 저장
3. TODO 목록 생성 → `todo.md` 저장

### 7️⃣ 결과 확인
생성된 세 개의 마크다운 파일을 확인하고 ✨ 바이브코딩을 시작하세요!

## 📁 생성되는 파일

### `prd.md` - 제품요구사항문서
- 제품 개요 및 목표
- 대상 사용자 페르소나
- 사용자 스토리 및 유스케이스
- 기능적/비기능적 요구사항
- 성공 측정 기준
- 로드맵 및 일정

### `trd.md` - 기술요구사항문서
- 고수준 아키텍처
- 데이터 모델 및 스키마
- 기술 스택 및 라이브러리
- 보안 설계
- 성능 최적화 전략
- 테스트 전략

### `todo.md` - 개발 할일 목록
- 우선순위별 작업 분류
- 세부 작업 및 구현 가이드
- 작업 간 의존성
- 완료 기준 및 검증 방법
- 실행 순서 및 타임라인

## ⚙️ 설정 옵션

### 모델 설정
각 단계별로 다른 OpenAI 모델 사용 가능:
- `gpt-5`: 최신 모델, 최고 품질 (권장)
- `gpt-4`: 고품질, 상세한 결과

### Verbosity 레벨
- `low`: 간결한 결과
- `high`: 상세한 결과

### Reasoning Effort
- `minimal`: 빠른 생성
- `high`: 더 정교한 분석

## 🛠️ 기술 스택

- **Node.js**: 런타임 환경
- **OpenAI API**: AI 텍스트 생성
- **Commander.js**: CLI 인터페이스
- **Inquirer.js**: 인터랙티브 질문
- **Chalk**: 터미널 색상 출력
- **Ora**: 로딩 스피너
- **dotenv**: 환경변수 관리

## 🚨 주의사항

- OpenAI API 사용으로 인한 비용이 발생할 수 있습니다
- `.env` 파일에 API 키를 안전하게 보관하세요
- 생성된 문서는 프로젝트에 맞게 추가 검토 및 수정이 필요할 수 있습니다

## 🔧 트러블슈팅

### 자주 발생하는 문제

#### API 키 관련 오류
```
Error: OpenAI API key not found
```
**해결방법**: `.env` 파일에 `OPENAI_API_KEY=your-key-here` 추가

#### 권한 오류
```
permission denied: ./vibedoc.js
```
**해결방법**: `chmod +x vibedoc.js` 실행

#### 의존성 설치 실패
**해결방법**: Node.js 버전 확인 및 캐시 정리
```bash
node --version  # 14.0.0 이상 확인
npm cache clean --force
npm install
```

### 디버그 모드
상세한 로그가 필요한 경우:
```bash
vibedoc --verbose
```

## 🤝 기여하기

### 개발 환경 설정
```bash
# 저장소 포크 후 클론
git clone https://github.com/yourusername/vibedoc.git
cd vibedoc
npm install

# 개발 모드로 실행
npm run dev
```

### 기여 가이드라인
1. 이슈를 먼저 생성하여 논의
2. Feature branch 생성 (`git checkout -b feature/amazing-feature`)
3. 변경사항 커밋 (`git commit -m 'Add amazing feature'`)
4. Branch에 푸시 (`git push origin feature/amazing-feature`)
5. Pull Request 생성

### 코딩 스타일
- ESLint 설정 준수
- 한국어 주석 및 메시지 사용
- 타입 안정성을 위한 JSDoc 주석 권장

## 📞 지원 및 문의

- **버그 리포트**: [GitHub Issues](https://github.com/username/vibedoc/issues)
- **기능 요청**: [GitHub Discussions](https://github.com/username/vibedoc/discussions)
- **이메일**: contact@vibedoc.dev

## 🗺️ 로드맵

### v1.1.0 (예정)
- [ ] 다국어 지원 (영어)
- [ ] 커스텀 템플릿 지원
- [ ] 웹 인터페이스 추가

### v1.2.0 (예정)
- [ ] Notion, Confluence 내보내기
- [ ] 협업 기능
- [ ] 프로젝트 히스토리 관리

## 📄 라이선스

AGPL-3.0

## 🤝 기여

이슈 리포트 및 풀 리퀘스트를 환영합니다!

## 🎯 CLI 옵션

### 기본 명령어
```bash
vibedoc                    # 대화형 문서 생성 시작
vibedoc help               # 상세 사용법 도움말
```

### 옵션
- `-v, --verbose`: 상세 출력 모드 (디버깅 정보 포함)
- `-q, --questions <number>`: 질문 횟수 설정 (기본값: 10, 범위: 1~50)
- `--skip-trd`: TRD 문서 생성 건너뛰기
- `--skip-todo`: TODO 목록 생성 건너뛰기
- `--version`: 버전 정보 표시
- `--help`: 도움말 표시

### 사용 예시
```bash
# 기본 실행 (PRD → TRD → TODO 순서로 모든 문서 생성)
vibedoc

# 상세 모드로 실행 (진행 상황과 디버그 정보 표시)
vibedoc --verbose

# 질문 횟수를 5개로 줄여서 빠르게 생성
vibedoc -q 5

# 질문 횟수를 20개로 늘려서 상세하게 생성
vibedoc --questions 20

# PRD만 생성하고 TRD, TODO는 건너뛰기
vibedoc --skip-trd

# PRD, TRD만 생성하고 TODO는 건너뛰기
vibedoc --skip-todo

# 질문 5개 + 상세 모드 + TRD 건너뛰기
vibedoc -q 5 -v --skip-trd
```

## 💡 사용 예시

```bash
$ vibedoc
🚀 VibeDOC - Vibe Document Generator
쉽게 PRD, TRD, TODO List를 만들 수 있는 문서 생성 도구

? 만들고자 하는 프로젝트에 대해 간단히 설명해주세요: 사진을 첨부할 수 있는 개인 일기장 웹앱

[1/10] ? 주요 사용자층은 누구인가요?
❯ 개인 사용자
  소규모 팀
  기업 사용자
  교육 기관

...질문 진행...

✅ 설문이 완료되었습니다!
🔄 PRD 문서를 생성하고 있습니다...
✅ PRD 생성 완료: prd.md
🔄 PRD를 바탕으로 TRD(기술요구사항문서)를 생성하고 있습니다...
✅ TRD 생성 완료: trd.md
🔄 TRD를 바탕으로 TODO 목록을 생성하고 있습니다...
✅ TODO 변환 완료: todo.md

🎉 전체 문서 생성이 완료되었습니다!
생성된 파일들:
  • prd.md - 제품요구사항문서
  • trd.md - 기술요구사항문서  
  • todo.md - 개발 할일 목록

✨ 이제 바이브코딩을 시작할 준비가 되었습니다!
```