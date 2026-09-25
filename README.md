# PromptPro · RT-CFCG 프롬프트 진단기

사용자가 입력한 프롬프트의 골격을 **RT-CFCG** 6요소로 분석·최적화하는 단일 페이지 웹앱입니다.

| 키 | 요소 | 설명 |
|---|---|---|
| R | 역할 (Role) | AI에게 부여할 전문가 역할 |
| T | 임무 (Task) | 수행할 구체적 작업 |
| C | 맥락 (Context) | 상황·배경·대상 |
| F | 포맷 (Format) | 결과물 형태·구조·분량 |
| C | 제약조건 (Constraints) | 금지사항·규칙·톤 |
| G | 목표 (Goal) | 최종 달성 목적 |

## 기능
- **요소별 진단 & 해부**: 6요소별 충족/보완 필요/누락 판정, 원문 인용, 피드백, 종합 점수
- **프롬프트 최적화**: 간결하게, 요소별로 재구성한 프롬프트 + 변경 사항 + 복사
- **프롬프트 구조 해부도**: 표준 예시 / 내 분석 결과 비교

## 실행
빌드 없이 `index.html`을 브라우저로 열면 됩니다. (GitHub Pages·Vercel 정적 배포 가능)

## AI 연결 (Claude)
- 우측 상단 ⚙ → Claude API 키(`sk-ant-...`) 입력 시 Claude로 분석 (기본 모델 `claude-opus-5`)
- Anthropic TypeScript SDK(`@anthropic-ai/sdk`)를 jsDelivr ESM으로 불러와 브라우저에서 직접 호출합니다 (`dangerouslyAllowBrowser: true`)
- 응답은 JSON Schema 구조화 출력(`output_config.format`)으로 받습니다
- `claude-opus-5` 사용 시 서버측 거절 폴백(`fallbacks: "default"`)을 켭니다
- 키가 없으면 내장 규칙 기반 분석기로 동작
- 키는 브라우저 localStorage에만 저장됩니다. 브라우저에서 직접 호출하는 방식이라 공개 서비스로 배포할 때는 서버(프록시)를 두는 구성이 필요합니다.
