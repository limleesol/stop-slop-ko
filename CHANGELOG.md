# Changelog

버전은 의미 변화 기준. / Versions track meaningful changes. (KO / EN)

## [0.8.0] - 2026-07-06

실사용 관찰 기반 패턴 3종 추가, Claude Code 스킬 로딩 호환성 정리. / Three patterns from real-world usage observations; Claude Code skill-loading compatibility cleanup.

- **추가/Added** 줄표(—) 남용 패턴 — 영어 em dash 문체의 직수입, 문단당 1개 이하 기준. / Em-dash overuse pattern — imported from English LLM style; at most one per paragraph.
- **추가/Added** 불릿 나열 의존 패턴 — 서술 문단이 뼈대, 불릿·표는 보조. / Bullet-list dependence pattern — prose paragraphs as the skeleton, bullets/tables as support.
- **변경/Changed** 이분법 대조 규칙 확대 — "단순히" 없는 일반형 `X가 아니라 Y다`와 대조문 연쇄(2회 이상 반복) 금지 명시. / Extended the false-dichotomy rule to the plain "not X but Y" form and to stacked contrastive sentences.
- **변경/Changed** 동어반복 부연에 문단 단위 기준 추가 — 새 정보 없는 문단은 삭제 후보. / Restatement rule now applies at paragraph level — paragraphs adding no new information are deletion candidates.
- **변경/Changed** description 트리거에 "윤문", "퇴고", "리라이팅", "매끄럽게" 키워드 추가. / Added "윤문/퇴고/리라이팅/매끄럽게" (polish/rewrite) keywords to the trigger description.
- **변경/Changed** frontmatter에서 비표준 `metadata` 블록 제거(Claude Code 스킬 로더 호환), 저자 정보는 본문 출처 절로 이동. / Removed the non-standard `metadata` frontmatter block for Claude Code skill-loader compatibility; author info moved to the Sources section.

## [0.7.0] - 2026-06-03

[관찰]/[규범] 분류 복구, 날조 금지 규칙 준수하도록 예시 교정, 레지스터 보존을 위한 복수 교정안 추가, 트리거 평가 파일명 변경 반영. / Restored [norm]/[observed] tagging, aligned examples with the no-fabrication rule, added multi-register outputs, updated trigger eval filename references.

- **복구/Restored** SKILL.md 및 README.md 내 `[관찰]`/`[규범]` 태그 분류 복구. / Restored `[observed]`/`[norm]` pattern classifications.
- **수정/Fixed** 예시 4, 5, 6: 원문에 없는 정보(구체적 숫자 및 대안 논리)를 지어내어 기술하던 모순을 해결하고 '날조 금지' 철칙에 맞게 교정. / Aligned examples 4, 5, and 6 with the no-fabrication rule by removing invented facts.
- **수정/Fixed** 예시 1, 4, 5, 6: 글의 소통 목적을 보존할 수 있도록 레지스터별(보고서용 vs 대화형/제안용 등) 복수 교정안(After) 제시. / Added multi-register alternatives (report vs conversational/proposal) to preserve communicative intent.
- **수정/Fixed** 예시 8, 10: 원문이 존댓말일 경우 교정안에서도 존댓말 레지스터가 그대로 유지되도록 수정 (반말 획일화 방지). / Fixed examples 8 and 10 to preserve polite style (존댓말) instead of converting to plain style.
- **변경/Changed** README.md 내 트리거 데이터셋 참조 파일명 수정 (`eval_set.json` → `trigger_eval.json`). / Updated trigger dataset file references in README.md.

## [0.6.0] - 2026-06-02

eval 프레임워크 구축, 예시 오류 수정, 레지스터 감지 단계 추가, description 최적화. / Eval framework, example fixes, register detection step, description optimization.

- **추가/Added** `evals/evals.json` — 5개 구조화 테스트 케이스(어설션 포함): 보고서 slop, 칼럼 slop, 수치 보존, 과교정 함정, 레지스터 유지. / 5 structured test cases with assertions: report slop, column slop, data preservation, overcorrection trap, register preservation.
- **추가/Added** SKILL.md 0단계: 교정 전 원문 레지스터(격식 보고서·대화체·에세이·메모) 파악 단계. / Step 0: identify source register (formal report, conversational, essay, memo) before editing.
- **수정/Fixed** 예시 1: Before에 실제 내용 없어 After 주제가 달라지던 문제 수정. / Example 1: Before had no content, causing After to shift topic.
- **수정/Fixed** 예시 3: After에 원문에 없는 수치(23%, 3분기) 날조 — 스킬 자체 날조 금지 규칙과 모순. 수치 제거, 공허한 수식어 걷어낸 결과만 남김. / Example 3: fabricated specifics (23%, Q3) not in source, contradicting the skill's no-fabrication rule. Removed invented numbers.
- **변경/Changed** description 전면 개정 — 트리거 발동률 0% → 예측 ~100%. 구체적 slop 표현과 발동 시나리오 3가지, 제외 케이스 명시. / Description rewritten: trigger rate ~0% → ~100%. Lists specific slop phrases, 3 trigger scenarios, explicit exclusions.


## [0.5.0] - 2026-06-02

eval에서 드러난 두 실패 패턴(과교정·날조)을 막는 가드 추가. / Guards against two failure modes found in eval (over-correction, fabrication).

- **추가/Added** "철칙: 지우되 만들지 마라" 섹션(정보 보존·무날조)을 규칙 앞에 배치. / A "delete, don't invent" preamble (preserve information, no fabrication) placed before the rules.
- **추가/Added** 예시 10(날조 vs 올바른 교정). / Example 10 (fabrication vs correct edit).
- **변경/Changed** 규칙 6: 추상어 구체화는 원문에 근거가 있을 때만, 없으면 삭제만. / Rule 6: make abstractions concrete only when the source supports it; otherwise delete.
- **변경/Changed** 규칙 11: 출력 전 길이·리듬 점검(원문 절반 이하면 정보 손실 신호). / Rule 11: pre-output length/rhythm check (under half the source length signals information loss).
- **변경/Changed** 채점에 "보존" 항목 추가, 6점 미만이면 점수와 무관하게 재작성. / Added a "preservation" scoring item; under 6 forces a rewrite regardless of total.

## [0.4.0] - 2026-06-02

reference 분리 구조를 단일 파일로 통합. / Consolidated the split reference structure into one file.

- **변경/Changed** references/(phrases·structures·examples)를 SKILL.md로 병합, 중복 제거. / Merged references/ (phrases, structures, examples) into SKILL.md and de-duplicated.
- **제거/Removed** references/ 디렉터리. / The references/ directory.
- **근거/Rationale** eval 20실행(통합 vs 분리): 분리본 reference 미열람(0/20), 품질 동률(제거율 100% vs 99%), 통합본 실행당 토큰 약 50% 증가. 상세 표의 한계 효용이 낮음을 확인. / 20-run eval (merged vs split): split references never read (0/20), equal quality (100% vs 99% marker removal), merged uses ~50% more tokens per run. Detailed tables shown to have low marginal value.

## [0.3.0] - 2026-06-02

"정확성 ≠ slop" 진단 후 구조 개편. / Restructured after diagnosing "correctness ≠ slop."

- **변경/Changed** slop 규칙을 핵심으로, 바른 한국어(이중피동·번역투)는 "정확성 축" 부록으로 분리. / Slop rules become the core; correctness (double passives, translationese) moved to an appendix.
- **추가/Added** 담화 단위 패턴 — 양비론·동어반복·메타담화·정의로 시작·막연한 권위 호소. / Discourse-level patterns — both-sidesing, restatement, meta-discourse, opening with a definition, vague authority.
- **추가/Added** 규칙 11 "한 문체로 수렴하지 마라"(가장 중요). / Rule 11 "don't converge to one voice" (most important).
- **추가/Added** 감정 과장 형용사, 채점 "목소리" 항목. / Exaggerated adjectives; a "voice" scoring item.
- **제거/Removed** 한자어 순화 섹션 — 순화는 slop 신호가 아니고 레지스터를 납작하게 만들어 새 slop을 유발. / The Sino-Korean purification section — purification is not a slop signal and flattens register into new slop.

## [0.2.0] - 2026-06-02

패턴 보강. / Pattern expansion.

- **추가/Added** 접속부사 전체 목록(인과·첨가·전환). / Full connective-adverb list (causal, additive, transitional).
- **추가/Added** AI 클리셰(의의·시사점, 패러다임 과장, 시대 상투어). / AI clichés (significance/implication, paradigm hype, era tropes).
- **추가/Added** 번호 열거(`첫째/둘째/셋째`)와 번호가 정당한 경우 기준. / Numbered enumeration and when numbering is justified.

## [0.1.0]

초기 버전. / Initial version.

- SKILL.md + references/(phrases·structures·examples) 분리 구조, 핵심 패턴 약 70개, [규범]/[관찰] 표기. / Split SKILL.md + references/ structure, ~70 core patterns, [norm]/[observed] tagging.
- Hardik Pandya의 stop-slop에서 영감, 한국어 패턴은 독립 재구성. / Inspired by Hardik Pandya's stop-slop; Korean patterns rebuilt independently.
