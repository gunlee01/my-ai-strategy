# 코드 리뷰와 사람 검증은 사라지지 않는다

## 핵심 주장

AI를 잘 활용한다는 것은 사람이 코드를 전혀 보지 않아도 된다는 뜻이 아니다.

오히려 AI를 깊게 활용할수록 사람은 더 높은 수준에서 코드 구조, 요구사항 충족, 영향 범위, 운영 리스크를 검토해야 한다.

AI가 코드를 더 빨리 만들수록 생성량은 늘어난다.
그러면 중요한 병목은 코드를 치는 시간이 아니라, 산출물을 이해하고 검증하고 책임질 수 있는가로 이동한다.

또한 SPEC, 테스트, 구현의 정렬을 계속 유지해야 한다.
코드가 엔지니어링 규율보다 빠르게 생산되면, 코드가 그럴듯하고 테스트를 통과해도 시스템 설명과 실제 구현이 어긋나는 spec drift가 빨라질 수 있다.

## 왜 코드 리뷰가 더 중요해지는가

AI가 만든 코드는 국지적으로 그럴듯할 수 있다.

더 중요한 위험은 AI 코드가 바로 실패하는 경우만이 아니다.

AI 코드는 테스트를 통과하거나 PR이 승인될 만큼 성공한 것처럼 보이면서도, 기존 구조를 무시하고 중복 로직을 쌓을 수 있다.
이 경우 문제는 즉시 장애로 드러나지 않고, 장기 유지보수 비용과 조용한 기술부채로 쌓인다.

하지만 아래 문제는 여전히 남는다.

- 요구사항을 정말 만족하는가.
- SPEC, 테스트, 구현이 서로 정렬되어 있는가.
- 기존 코드 구조와 패턴에 맞는가.
- 모듈 경계와 데이터 흐름을 깨지 않는가.
- 권한, 보안, 운영 리스크를 만들지 않는가.
- 기존 함수를 재사용하지 않고 중복 로직을 새로 만들지는 않았는가.
- AI가 만든 변경량이 사람이 한 번에 리뷰할 수 있는 범위를 넘지는 않았는가.
- 테스트에는 없지만 실제 유저 플로우에서 깨지는 부분은 없는가.
- 이 변경이 다른 기능에 어떤 영향을 주는가.

그래서 사람의 리뷰는 없어지는 것이 아니라 성격이 바뀐다.

라인 바이 라인으로 모든 코드를 같은 밀도로 읽는 방식에서, 구조, 의미, 영향 범위, 운영 리스크를 검토하는 방식으로 이동한다.

## 실무 근거

AI를 많이 쓰는 현장에서도 사람 검증의 중요성이 반복해서 나온다.

- Harness 2026 조사에서는 AI 도입 후 코드 리뷰 시간이 늘었다는 응답이 많고, AI 생성 코드 리뷰와 버그 수정 같은 보이지 않는 작업이 개발자 시간을 크게 차지한다고 설명한다.
  - https://www.harness.io/press-and-news/ai-has-outpaced-how-engineering-organizations-measure-developer-productivity
- GeekNews가 정리한 "AI는 소프트웨어 엔지니어링을 단순화하지 않았다" 글은 LLM이 코드 작성 속도를 높였지만 시스템 설계, 명세, 검증, 일관성 유지의 복잡성은 줄이지 못했고, 코드 생산이 엔지니어링 규율보다 빨라지면 spec drift가 가속된다고 설명한다.
  - https://news.hada.io/topic?id=27510
- RosettaLens의 에이전틱 엔지니어링 번역은 바이브 코딩과 에이전틱 엔지니어링을 구분한다.
  에이전틱 엔지니어링은 SPEC으로 시작하고, 모든 diff를 리뷰하고, 테스트를 실행하며, 인간이 아키텍처와 품질과 정확성을 책임지는 방식이다.
  - https://rosettalens.com/s/ko/agentic-engineering
- "Agentic Coding is a Trap"은 AI agent가 만든 수천 줄을 문제되기 전에 볼 수 있으려면 숙련 개발자의 비판적 사고와 아키텍처 판단이 필요하다고 지적한다.
  또한 한 번에 리뷰할 수 있는 양보다 많이 생성하지 말고, 너무 많으면 속도를 늦추고 작업을 쪼개야 한다고 제안한다.
  - https://larsfaye.com/articles/agentic-coding-is-a-trap
- RPCS3 README의 AI Use 정책은 AI 사용 자체를 금지하는 것이 아니라, 작성자가 이해하지 못하고 테스트하지 않은 AI-generated slop을 maintainer에게 떠넘기는 것을 금지한다.
  제출자는 모든 코드를 완전히 소유하고 이해해야 하며, AI agent나 자동화 도구가 연 PR은 AI 관여 범위와 human testing/review 내용을 disclosure해야 한다.
  - https://github.com/RPCS3/rpcs3#ai-use
- OpenAI Codex의 GitHub code review 문서도 Codex review를 human merge approval의 대체가 아니라, human review 전에 regression, missing tests, documentation issue를 찾는 보조 review signal로 설명한다.
  - https://developers.openai.com/codex/use-cases/github-code-reviews
- MSR 2026의 More Code, Less Reuse 연구는 AI agent PR이 pass rate만으로는 괜찮아 보여도, 코드 재사용 기회를 놓치고 중복 코드를 더 많이 만들 수 있다고 보고한다.
  이 연구는 표면적으로 그럴듯한 AI 코드가 중복과 조용한 기술부채를 숨길 수 있음을 보여준다.
  - https://arxiv.org/abs/2601.21276
  - https://2026.msrconf.org/details/msr-2026-mining-challenge/62/More-Code-Less-Reuse-Investigation-on-Code-Quality-and-Reviewer-Sentiment-towards-A
- Sonar 2026 State of Code는 AI 생성 코드가 폭증했지만, 신뢰와 검증 병목이 새롭게 생겼다고 설명한다.
  - https://www.sonarsource.com/state-of-code-developer-survey-report.pdf
- TechCrunch의 2025 기사도 AI를 극한까지 쓰는 숙련 개발자가 결국 AI 산출물을 다시 쓰고 사실 확인하는 역할을 맡게 된다고 설명한다.
  - https://techcrunch.com/2025/09/14/vibe-coding-has-turned-senior-devs-into-ai-babysitters-but-they-say-its-worth-it/
- Stack Overflow 2025 조사는 AI 사용은 늘었지만 신뢰는 낮아졌고, almost-right AI 코드 수정과 사람 검증 필요성이 핵심 이슈라고 설명한다.
  - https://stackoverflow.blog/2025/12/29/developers-remain-willing-but-reluctant-to-use-ai-the-2025-developer-survey-results-are-here/

이 근거들은 모두 같은 방향을 가리킨다.

AI를 쓰지 말자는 것이 아니다.
AI를 제대로 쓰려면 사람 검토와 검증 구조가 더 중요해진다는 것이다.

## 말하기용 답변

AI가 코드를 잘 만든다고 해서 사람이 코드를 전혀 안 봐도 된다는 뜻은 아닙니다.

오히려 AI를 많이 쓸수록 코드와 문서 산출물이 더 많이 나오기 때문에, 사람이 구조와 의미 단위로 더 잘 봐야 합니다.

AI 코드는 실패해서만 위험한 것이 아닙니다.
성공한 것처럼 보이면서 기존 구조를 무시하고 중복 로직을 쌓을 수 있기 때문에 위험합니다.

이제 모든 라인을 같은 밀도로 직접 쓰고 읽는 방식은 줄어들 수 있습니다.
하지만 요구사항을 만족하는지, SPEC과 테스트와 구현이 정렬되어 있는지, 기존 구조와 맞는지, 권한이나 데이터 흐름을 깨지 않는지, 재사용해야 할 코드를 중복 구현하지 않았는지, 운영 리스크가 없는지는 사람이 봐야 합니다.

에이전틱 엔지니어링은 바이브 코딩과 다릅니다.
SPEC으로 시작하고, 사람이 모든 diff를 리뷰하고, 테스트를 돌리고, 시스템의 주인으로 남는 방식입니다.
AI가 만든 양이 한 번에 리뷰할 수 있는 범위를 넘으면 속도를 늦추고 작업을 쪼개야 합니다.

최근 조사들도 같은 방향을 보여줍니다.
AI 도입 후 코드 리뷰와 검증 시간이 늘고, senior 개발자들이 AI 산출물을 고치고 검증하는 부담을 많이 지고 있습니다.

오픈소스 프로젝트의 정책도 같은 방향입니다.
RPCS3는 AI 사용 자체가 아니라, 작성자가 이해하지 못하고 테스트하지 않은 코드를 maintainer에게 떠넘기는 것을 금지합니다.
OpenAI Codex 문서도 Codex 리뷰를 human merge approval의 대체가 아니라, 사람 리뷰 전의 보조 신호로 설명합니다.

그래서 결론은 "코드 리뷰가 필요 없다"가 아니라 "코드 리뷰의 초점이 라인 단위에서 구조, 의미, 맥락, 재사용성, 영향 범위 단위로 올라간다"입니다.

## 한 문장 요약

> AI 시대에도 코드를 안 보는 것이 아니라, 사람이 구조와 의미와 영향 범위 단위로 더 책임 있게 봐야 한다.
