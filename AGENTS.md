# AI Strategy Project

## 프로젝트 목적

이 프로젝트는 사용자의 AI 전략에 대한 고민을 기록하고 정리하는 공간이다.

여기에는 문제의식, 관찰, 가설, 판단 기준, 반론, 리스크, 실행 아이디어, 참고 자료, 대화 중 떠오른 생각을 남긴다.
목표는 단순한 결론 요약이 아니라, 사용자의 생각이 어떻게 이어지고 바뀌었는지를 보존하는 것이다.

작업의 원천 자료는 Markdown 문서다.
Markdown에는 생각의 흐름, 근거, 결정, 미해결 질문을 구조적으로 남긴다.

최종 산출물은 구조적이고 인터랙티브한 HTML 사고 지도다.
이 HTML만 보면 사용자가 어떤 AI 전략 고민을 했고, 어떤 논리로 생각을 정리했는지 빠르게 파악할 수 있어야 한다.

## 최종 HTML의 기본 구조

최종 HTML은 다음 순서로 사고를 따라갈 수 있어야 한다.

1. 큰 흐름
   - AI 전략 고민의 전체 맥락, 핵심 문제의식, 주요 주장, 판단 축을 먼저 보여준다.
   - 사용자가 머릿속에 전체 지도를 먼저 만들 수 있어야 한다.

2. 생각의 연결망
   - 큰 흐름의 각 지점에서 세부 근거, 관찰, 가설, 반론, 리스크, 실험, 결정으로 내려갈 수 있어야 한다.
   - 사용자가 왜 그런 판단에 도달했는지 추적할 수 있어야 한다.

3. 질문 대응 모드
   - 회의, 발표, 의사결정, 토론 상황에서 바로 꺼내 쓸 수 있는 답변 프레임을 보조적으로 제공한다.
   - 한 문장 답변, 짧은 설명, 예상 질문, 반론 대응을 포함할 수 있다.

## 시각화 원칙

복잡한 구조나 흐름은 텍스트만으로 설명하지 않는다.

이해를 돕기 위해 필요한 경우 SVG 흐름도, Canvas 기반 인터랙티브 맵, 관계도, 분기 다이어그램을 HTML에 포함한다.

시각화는 장식이 아니라 생각의 구조를 복원하기 위한 도구여야 한다.
관계, 흐름, 분기, 의존성, 판단 기준이 더 명확해질 때만 사용한다.

## 작업 원칙

- 큰 흐름을 먼저 잡고, 필요한 곳에서 디테일로 내려간다.
- 기록은 최종 결론뿐 아니라 생각이 형성된 과정까지 남긴다.
- 문서는 나중에 말하기, 회의 준비, 전략 정리, 의사결정 설명에 바로 쓸 수 있어야 한다.
- HTML은 읽는 문서이면서 동시에 생각을 다시 떠올리는 도구여야 한다.
- 새로운 자료나 아이디어가 들어오면 기존 구조 안에서 어느 위치에 연결되는지 함께 정리한다.

## 문서 구조

다른 세션에서도 일관되게 이어서 작업할 수 있도록 아래 구조를 기본으로 사용한다.

```text
notes/
  inbox/
    YYYY-MM-DD-<topic>-raw-thoughts.md
  big-flow.md
  nodes/
    <topic>.md
  questions/
    <topic>.md
```

### inbox

`notes/inbox/`는 사용자가 처음 쏟아낸 생각을 원문에 가깝게 보존하는 공간이다.

여기서는 문장을 과하게 정제하지 않는다.
생각의 출발점, 말투, 반복, 불확실성, 당시의 문제의식을 남기는 것이 중요하다.

### big-flow.md

`notes/big-flow.md`는 현재까지 정리된 가장 중요한 큰 흐름이다.

새 세션에서 전체 맥락을 파악할 때는 먼저 이 문서를 읽는다.
사용자의 중심 주장, 핵심 논리, 비유, 개념 정의, 최종 HTML 구조 후보가 여기에 있어야 한다.

### nodes

`notes/nodes/`는 개별 개념, 주장, 비유, 근거를 분리해 정리하는 공간이다.

예를 들면 `ai-limits.md`, `human-in-the-loop.md`, `barn-vs-building.md`, `verification-harness.md`처럼 하나의 생각 덩어리를 독립 문서로 관리한다.

큰 흐름에서 어떤 부분이 복잡해지면 `nodes`로 승격한다.

### questions

`notes/questions/`는 회의, 발표, 토론, 의사결정 상황에서 바로 꺼내 쓸 수 있는 Q&A 문서다.

각 질문은 가능하면 아래 구조를 따른다.

```text
질문
  ↓
답변 프레임
  ↓
말하기용 답변
  ↓
핵심 한 줄
```

현재 개발자 대체론 관련 질문 대응은 `notes/questions/ai-developer-replacement.md`에 정리되어 있다.

## 현재 주요 문서

- `notes/big-flow.md`
  - 현재까지의 중심 주장과 큰 흐름.
  - "AI는 하방을 높이지만 상방을 높이지 못한다"를 기준으로 전체 논리를 정리한다.

- `notes/questions/ai-developer-replacement.md`
  - 개발자 대체론, 코드 리뷰 생략, QA 책임, 컨텍스트 한계, 생산성/무인화 구분에 대한 말하기용 Q&A.

- `notes/questions/leader-facing-qa.md`
  - 리더/의사결정자에게 AI 생산성, 10배 생산성 주장, 인원 축소 논리를 설명하기 위한 말하기용 Q&A.

- `notes/questions/practitioner-facing-qa.md`
  - 개발자/개발 조직 실무자가 AI 개발을 실제로 수행할 때 필요한 SPEC, 작업 분해, 검증 루프, 코드 리뷰, 유저 관점 확인 중심의 Q&A.

- `notes/nodes/productivity-shift-and-10x-myth.md`
  - AI가 직접 작성 시간을 지시/검토/검증 시간으로 이동시킨다는 생산성 전환 모델과 10배 생산성 신화에 대한 정리.

- `notes/nodes/role-replacement-illusion.md`
  - AI가 다른 역할의 표면적 산출물을 쉽게 만들게 하면서 역할 전체가 필요 없어 보이는 착각을 만든다는 논리.

- `notes/nodes/ai-delegation-criteria.md`
  - AI에게 맡길 일과 사람이 봐야 할 일을 검증 가능성, 실패 비용, 맥락 의존성, 책임 규모로 나누는 기준.

- `notes/nodes/barn-vs-building.md`
  - "유튜브 보고 이것저것으로 만든 헛간"과 "고층 빌딩 오피스"의 책임 규모 차이를 설명하는 핵심 비유.

- `notes/nodes/unverified-complexity-risk.md`
  - AI 산출물이 빠르게 늘어날 때 검증되지 않은 복잡도가 뒤로 쌓이고 품질 비용으로 터지는 리스크.

- `notes/nodes/operational-incident-and-fix-loop.md`
  - 운영 중 중요한 시스템에서는 "고쳐줘" 반복이 아니라 담당자가 코드 구조를 이해하고 AI와 함께 원인/영향 범위를 좁혀 정밀하게 수정해야 한다는 논리.

- `notes/nodes/effective-ai-engineering-org.md`
  - AI 산출물을 명확한 SPEC, 강한 검증 루프, 사람의 검토 책임, 측정 학습 체계로 안정적으로 흡수하는 조직의 모습.

- `notes/nodes/human-code-review-and-verification.md`
  - AI 시대에도 코드를 전혀 안 봐도 되는 것이 아니며, 사람 코드 리뷰와 구조/의미/영향 범위 검증이 더 중요해진다는 주장과 근거.

- `notes/nodes/qa-responsibility-and-agentic-engineering.md`
  - QA는 개발자 책임을 대체하지 않는다는 주장과, 바이브코딩과 에이전틱 엔지니어링의 차이를 정리한 node.

## 세션 시작 시 참조 순서

새로운 세션에서 이 프로젝트를 이어서 작업할 때는 아래 순서로 확인한다.

1. `AGENTS.md`
   - 프로젝트 목적, 최종 HTML 방향, 문서 구조를 확인한다.

2. `notes/big-flow.md`
   - 현재까지의 중심 주장과 큰 논리 흐름을 확인한다.

3. `notes/questions/`
   - 질문 대응, 말하기용 답변, 대상 독자별 설명 프레임을 확인한다.

4. `notes/inbox/`
   - 원문 맥락이나 생각의 출발점이 필요할 때 확인한다.

5. `notes/nodes/`
   - 특정 개념이나 비유가 별도 문서로 승격되어 있을 때 확인한다.

## 정리 방식

새로운 생각이 들어오면 바로 결론 문서에 덮어쓰지 않는다.

먼저 `inbox`에 원문을 보존하고, 인터뷰나 정리를 통해 `big-flow`, `nodes`, `questions` 중 적절한 위치로 승격한다.

기존 주장과 충돌하는 내용이 나오면 조용히 덮어쓰지 말고, 충돌 지점과 바뀐 이유를 문서에 남긴다.

최종 HTML은 `big-flow -> nodes drill-down -> questions mode` 구조를 기본으로 삼는다.

## 최종 HTML 산출물

현재 최종 one-page HTML 사고 지도 원본은 `docs/ai-strategy-framework.html`이다.

GitHub Pages 배포용 구조를 그대로 원본 구조로 사용한다.

- `docs/index.html`
  - GitHub Pages 진입점이다.
  - `./ai-strategy-framework.html`로 이동하는 redirect 파일이다.
- `docs/ai-strategy-framework.html`
  - 실제 one-page HTML이자 source of truth다.
  - HTML을 수정할 때는 이 파일을 직접 수정한다.

이 파일은 AI 전략에 대한 사용자의 최종 프레임워크를 한 페이지에서 복원하기 위한 산출물이다.
큰 흐름, 판단 시뮬레이터, 운영 중 "고쳐줘" 반복의 한계, 리더/실무자/개발자 대체론 Q&A, 개념 노드, 말하기 치트시트를 모두 포함한다.

새 세션에서 HTML을 수정해야 할 때는 아래 원칙을 지킨다.

- `notes/big-flow.md`, `notes/questions/`, `notes/nodes/`를 먼저 확인한다.
- `docs/ai-strategy-framework.html`을 직접 수정한다.
- 루트에는 별도의 `ai-strategy-framework.html` 사본을 두지 않는다.
- GitHub Pages는 `docs/` 폴더를 기준으로 서빙하는 구조로 본다.
- 큰 흐름을 먼저 보여주고, 세부는 필요할 때 펼치는 구조를 유지한다.
- Q&A 예시는 누락하지 않고 한 페이지 안에 유지한다.
- 핵심 원칙인 "사람이 여전히 개입해야 한다"를 흐리지 않는다.
- "헛간과 고층 빌딩" 비유는 핵심 비유로 취급한다. 초반 설명, 역할 대체 착각, 개발자 대체론, QA 책임, 운영 장애 대응에서 반복적으로 연결해도 된다.
- 새 노드나 질문이 생기면 Markdown 원천 문서를 먼저 보강한 뒤 HTML에 반영한다.
