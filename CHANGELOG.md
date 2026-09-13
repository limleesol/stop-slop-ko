# Changelog

날짜는 YYYY-MM-DD. 버전은 의미 변화 기준. / Versions track meaningful changes. (KO / EN)

## [0.12.0] - 2026-09-14

실사용 교정에서 스킬을 적용한 뒤에도 남았던 유형 3개와, 목록 대조만으로 "고칠 게 없다"고 판정한 오판정을 반영. / Three pattern types that survived a real editing pass with the skill applied, plus the false "nothing to fix" verdict reached by pattern-list matching alone.

- **추가/Added** "영어 어휘·관용구 직역" 절(표현 단위) — 어휘 직역(`이 기계에서는`, `알려진`), 관용구 직역(`금방 질린다`, `그리는 게 전부다`), 구문 직역(무생물의 소유 구문, 동명사 주어). 판정은 "영어를 보지 않고 말했다면 이 단어를 골랐을까". 부록 B(조사·명사화)와 역할을 나눔. / New "English lexical and idiom calques" section — lexical, idiom and construction calques, judged by whether a Korean speaker would pick the word without the English in view; split from Appendix B, which covers particles and nominalization.
- **추가/Added** "개발 은어·공간 비유" 절(표현 단위) — `뜬다`·`죽으면`·`붙어 있다`·`그린다`·`올라간다`·`나간다`를 독자가 넓은 문서에서 문자 그대로의 표현으로. 개발자끼리의 메모·커밋 메시지·팀 위키·배포 체크리스트는 면제이며, 절 첫머리에서 면제부터 판정한다. / New "developer jargon and spatial metaphor" section — replaced with literal wording in documents for a broad audience; developer-only memos, commit messages and team wikis are exempt.
- **추가/Added** "전제 누락" 절(구조 단위) — 대상 독자가 모르는 원인·조건을 건너뛴 문장. 답이 글 안에 있으면 앞으로 옮기고 묻지 않으며, 없으면 철칙 2에 따라 채우지 않고 교정문 뒤에서 묻는다. 질문은 대상 독자가 다음 문장을 따라갈 수 없는 경우만, 한 번에 세 개 이하. 바로 뒤에 붙인 이유를 독자가 이해할 수 있는 문장과 에세이·칼럼·마케팅 카피의 의도적 생략은 면제. 교정문에는 원문에 없는 이유 문장을 넣지 않는다. 생성 모드에도 반영. / New "missing premise" section — move the premise forward when the text has it; otherwise never fill it in (iron rule 2) and ask after the edited text, at most three questions. Also applied to generation mode.
- **추가/Added** 검증 단계(교정 모드, 여러 문단이거나 공개할 글) — ① 원문·교정문 문장 단위 대조표로 삭제·교체·이동·추가를 기록하고, 근거 없는 추가는 되돌리고 사라진 정보는 복원. ② 서브에이전트를 쓸 수 있으면 교정 맥락 없이 원문·교정문·대상 독자·SKILL.md만 받은 리뷰어를 실행(요청문 예시 포함), 없으면 교정 메모 없이 따로 점검. ③ 리뷰 결과는 규칙에 맞는 것만 반영하고 제외 이유를 남김. ④ 출력 끝에 검증 결과 한 줄. 생성 모드는 공개할 글에 ②~④를 재료 대비 사실 대조로 적용. 처음 쓰는 사람도 교정 결과를 따로 검수하지 않아도 되게 하려는 절차. / Verification step for multi-paragraph or published text — a sentence-level source/edit diff table (revert unsupported additions, restore lost facts), an independent reviewer subagent that gets only the source, the edit, the target reader and SKILL.md (with a request template; a separate self-check where subagents are unavailable), filtered adoption of findings with reasons for rejections, and a one-line verification summary. Generation mode applies steps 2–4 against the user's source material. README explains what first-time users will see.
- **추가/Added** 읽기 시험 — "slop이 거의 없다"는 판정을 패턴 목록 대조만으로 내리지 않고, 대상 독자의 자리에서 직역·은어·전제 누락 세 가지를 확인한 뒤에만 내린다. 교정 모드 절차와 출력 전 필수 점검 표에 반영. / Read test — a "barely any slop" verdict now requires checking calques, jargon and missing premises from the target reader's seat, not pattern matching alone; wired into the edit procedure and the pre-output checklist.
- **변경/Changed** 0단계에서 레지스터와 함께 대상 독자(배경지식·은어 공유 여부)를 정한다. 새 판정 셋의 기준. / Step 0 now also sets the target reader, the yardstick for the three new judgments.
- **변경/Changed** 핵심 규칙 11개 → 14개("번역·독자" 묶음 12~14 추가). 사물 주어 판정에 소유·행위 동사는 직역 절로 보내는 안내 추가. description 트리거에 번역투·번역체·개발 은어 지적 추가. / Core rules 11 → 14; the false-agent rule now routes possession/action verbs to the calque section; description trigger now covers complaints about translationese and developer jargon.
- **수정/Fixed** 문서 자체의 AI 말투 정리 — Claude Fable 5.1과 Gemini 3.8 Flash가 따로 검토한 결과 중 규칙에 맞는 것만 반영. 직역(`발명하지`, `자동 미덕`, `싸다`, `시작되었다`, `기록되었다`), 은어·비유(`훑어 읽기가 죽는다`, `리듬 죽음`, `사촌`, `납작하게`, `기본 전역`), 출처 절만 존댓말이던 레지스터 불일치, 영어 실험 라벨(`with`/`without`)을 주어로 쓴 문장 등. 0.11.2에서 대비가 논점인 예외로 남긴 대조 구문 2건은 두 모델 모두 지적했지만 유지. / Cleaned AI-sounding phrasing in the skill's own documents, adopting only the findings from separate Claude Fable 5.1 and Gemini 3.8 Flash reviews that fit the rules; the two contrast constructions kept as exceptions in 0.11.2 stay despite both models flagging them.
- **추가/Added** eval 6케이스 — 직역, 독자가 넓은 문서의 은어와 개발자 메모 면제(쌍), 글에 없는 전제는 묻기와 글 안에 있으면 묻지 않기(쌍), 목록 패턴이 없는 번역체 문단에서의 "거의 없음" 오판정. (총 27케이스) / Six eval cases — calques, jargon vs. developer-memo exemption (pair), ask vs. don't ask for premises (pair), and the false "barely any slop" verdict on a calque-only paragraph. 27 cases total.

## [0.11.3] - 2026-07-30

전체 검토 반영 — 대화체 레지스터 면제 2건(오탐 수정), 상호 참조·형식·README 구조 정리. / Full-review pass — two conversational-register exemptions (false-positive fixes), cross-reference, formatting, and README structure cleanup.

- **수정/Fixed** 수사적 질문·독자 참여 요청 면제에 대화체 칼럼·블로그 추가 — 훅 질문과 말 걸기('이런 적 있죠?')는 그 레지스터의 문체로 유지하고, 연속 반복만 잡는다. / Rhetorical-question and reader-engagement exemptions now cover conversational columns/blogs — hook questions and direct address are kept as that register's voice; only consecutive repetition fires.
- **수정/Fixed** 승격 예외 상호 참조 복구 — 서론 선언 예외 라벨을 "유일한 주제 문장(승격)"으로 바꿔 표 slop 절의 참조("서론 선언 승격 예외")가 실제 라벨과 맞게 했다. / Restored the promotion cross-reference — the intro-declaration exception label now contains "promotion", matching the table-slop section's reference.
- **수정/Fixed** 규칙 적용 범위 절의 예시를 면제·전역 두 방향 쌍으로 재작성. / The rule-scope example now shows both directions: a per-rule exemption and a global rule that still applies.
- **변경/Changed** 표·목록 예고 문장 절을 다른 절과 같은 라벨 형식(설명/대신/예외/우선순위)으로 줄 분리 — 내용 변경 없음. / The table lead-in section reformatted into the shared label layout (description / instead / exception / precedence) with no content change.
- **변경/Changed** README 정리 — 배경 절 표기 정리(선행 공백·이중 공백·대문자 Slop)와 예시 순서를 slop 먼저·규범(부록) 뒤로 교체, 0.4.0 실험 기록을 details 블록으로 접음, 주요 패턴 목록에서 판정 원칙 2건 분리, 사용법 절의 실험 서술을 CHANGELOG 참조로 축소. / README cleanup — background-section notation fixes and example reordering (slop first, appendix norms after), the 0.4.0 experiment folded into a details block, the two judgment principles moved out of the pattern list, and the usage section's experiment narration reduced to a CHANGELOG reference.
- **추가/Added** eval 2케이스 — 대화체 블로그의 훅 질문·말 걸기 유지(면제 발동), 격식 보고서의 같은 유형 문장 삭제(면제 미적용). (총 21케이스) / Two eval cases — conversational-blog hook and direct address survive (exemption fires); the same sentence types in a formal report are removed (no exemption). 21 cases total.

## [0.11.2] - 2026-07-30

문서 자체를 스킬 규칙으로 전수 감사해 slop 제거. / Full self-audit of SKILL.md and README against the skill's own rules; slop removed from the documents' own voice.

- **수정/Fixed** README 벤치마크 문단 재작성 — 문단당 줄표 2개(자기 임계 위반), "조건을 모르는 블라인드" 동어반복, "~한 시대에 가치가 남는 지점" 수사 제거. / Rewrote the benchmark paragraph in README — two em dashes in one paragraph (violating the skill's own threshold), redundant phrasing, and a rhetorical closer removed.
- **수정/Fixed** SKILL.md 문서 목소리의 대조 구문 2건을 직접 서술로("점수를 매기지 않는다", "지어내는 순간 날조가 된다"), 철칙 1 재진술 1건을 참조로, 목록 예고 문장 1건 삭제. 남긴 대조 구문 2건(레지스터 파괴·다양성)은 대비가 논점인 예외로 판정. / Two antithesis constructions in the document's own voice rewritten as direct statements, one restatement of iron rule 1 replaced with a reference, one list lead-in removed; two remaining contrasts kept under the "contrast is the point" exception.
- **수정/Fixed** README eval 케이스 수 18 → 19 (0.11.1 회귀 케이스 반영 누락). / README eval count corrected to 19.

## [0.11.1] - 2026-07-30

줄표 규칙의 임계와 삭제 우선 충돌 해소. / Resolves the conflict between the em-dash threshold and the delete-first instruction.

- **수정/Fixed** 줄표 남용 기준에 우선순위 명시 — 문단당 1개 이하(임계) 안의 줄표는 남기고, 임계를 넘은 줄표만 지운다. 2026-07 벤치마크에서 스킬 적용 조건이 임계 안의 줄표를 지워 블라인드 판정 감점을 받은 실측(evals/benchmark/RESULTS.md)에 따른 수정. (#3) / Clarified precedence in the em-dash rule — dashes within the one-per-paragraph threshold stay; only excess dashes are deleted. Fixes the over-correction measured in the 2026-07 benchmark, where the skill-applied condition deleted an in-threshold dash and lost the blind judgment. (#3)
- **추가/Added** 회귀 방지 eval 1케이스 — 임계 안의 줄표가 살아남아야 통과. (총 19케이스) / One regression eval — an in-threshold dash must survive editing (19 cases total).

## [0.11.0] - 2026-07-30

표·목록 주변 slop 3패턴 추가 — 산문 중심이던 패턴 목록을 실무 문서(기획서·보고서·위키)로 확장. 기획서·명세 레지스터 신설, 불릿 나열 의존 면제에 기획서·명세 반영. / Three new patterns for slop around tables and lists, extending the prose-centric pattern list to workplace documents (specs, reports, wikis); new spec-document register, also reflected in the bullet-list-dependence exemption.

- **추가/Added** "표·목록 주변 slop" 절(구조 단위) — ① 표·목록 예고 문장: 삭제, 단 표의 정체를 알리는 유일한 단서면 소제목으로 승격(서론 선언 승격 예외와 같은 구조). ② 표 셀 문단화: 셀에는 핵심 구절만 남기고 서술은 표 아래 본문으로 이동(철칙 1 우선). ③ 표·산문 이중 서술: 표만 남기고, 산문에만 있는 정보는 보존. / New "slop around tables and lists" section (structural patterns) — (1) table lead-in sentences: delete, or promote to a heading when the sentence is the only clue to the table's identity (same structure as the intro-declaration promotion exception); (2) prose-paragraph cells: keep a key phrase in the cell, move the narration below the table (iron rule 1 wins); (3) table–prose double narration: keep the table only, preserving information found solely in the prose.
- **추가/Added** 0단계 레지스터 표에 "기획서·명세" 행 — 신호: 요구사항·규칙 서술, 표·목록 중심, 단정형 어미. 교정 후에도 표·목록 구조와 단정형 명세 문장을 유지. / New "spec document" row in the Step-0 register table — signals: requirement/rule statements, table/list-centric, declarative endings; keep the table/list structure and declarative spec sentences after editing.
- **추가/Added** eval 4케이스 — 표 예고 문장 삭제, 유일한 단서의 소제목 승격, 셀 문단화의 본문 이동(정보 보존), 표·산문 이중 서술 해소. / Four new eval cases — table lead-in deletion, sole-identity promotion to a heading, cell-prose relocation with information preserved, table–prose double narration resolved.

## [0.10.0] - 2026-07-29

규칙에 적용 범위(scope) 체계 도입, 레지스터별 오탐 수정, 범용 판정기(삭제 시험·기계 판정) 추가. / Introduced a per-rule scope system, fixed register-specific false positives, added generic tests (deletion test, mechanical check).

- **추가/Added** "규칙 적용 범위" 절 — 표기 없는 규칙은 모든 레지스터에 적용, 면제는 규칙 단위로 해당 규칙에 명시. 블록의 레지스터가 달라도 전역 규칙은 그대로 적용. / New "rule scope" section — untagged rules apply to every register; exemptions are declared per rule; block-level register changes never suspend global rules.
- **수정/Fixed** 레지스터별 오탐 5건 — 독자 참여 요청: 마케팅·SNS의 CTA는 정상, 공허한 연속 질문만 잡는다. 사물 주어: 개인 에세이·회고의 의도적 의인화 제외. 수사적 질문: 마케팅·SNS 훅 질문 면제. 불릿 나열 의존: 메모·요약, 기술 문서의 항목형 구조 면제. 과잉 경어: 이메일·공지의 정중한 어미 유지, 겹침만 축소. / Five register false positives — reader-engagement: marketing/SNS CTAs are legitimate, only hollow question chains fire; inanimate subject: deliberate personification in personal essays/retrospectives is exempt; rhetorical questions: marketing/SNS hooks exempt; bullet dependence: memo/summary and technical-doc list structures exempt; excessive honorifics: keep polite endings in email/notice, only reduce stacking.
- **수정/Fixed** 수사적 질문 — 마케팅 카피·SNS의 훅 질문 면제. 0단계 표의 "짧은 훅 유지"와 충돌하던 것을 일관되게 정리. / Rhetorical questions — marketing/SNS hook questions exempted, resolving the conflict with the Step-0 register table ("keep short hooks").
- **추가/Added** 삭제 시험 — 목록에 없는 표현의 범용 판정기. 지워서 잃는 정보가 없으면 slop, 있으면 보존(철칙 1 우선). / Deletion test — a generic judge for unlisted phrases: no information lost when deleted means slop; otherwise keep it (iron rule 1 wins).
- **추가/Added** 사물 주어 기계 판정 — 무생물 주어+판단·발화·의도 동사면 걸림, 서술·범위 동사(다루다·포함하다·구성되다)는 정상. 고침 경로 2개(사람 주어·명사구) 명시. / Mechanical check for inanimate subjects — inanimate subject + judgment/speech/intent verb fires; scope verbs are normal formal prose. Two fix paths (human subject, noun phrase).
- **추가/Added** 0단계 블록 단위 판정 — 인용 대사·공지 템플릿·인터뷰 발췌는 그 블록의 레지스터로 판정. / Block-level register judgment in Step 0 — quoted dialogue, notice templates, interview excerpts are judged by their own register.
- **추가/Added** 서론 선언 승격 예외 — 선언이 글의 주제를 알리는 유일한 문장이면 삭제 대신 주장 문장으로 재작성. / Intro-declaration promotion exception — when the declaration is the only topic sentence, rewrite it as a claim instead of deleting.
- **추가/Added** eval 6케이스 — 레지스터별 독자 질문(보고서 vs SNS), 사물 주어 정상·오탐 쌍, 반응 동사("시장은 반응했습니다") 판정, 서론 선언 승격. / Six new eval cases — reader questions by register (report vs SNS), inanimate-subject fire/no-fire pair, reaction-verb case ("the market reacted"), intro-declaration promotion.
- **추가/Added** README 유지보수 원칙 — 규칙·예시를 고칠 때 그 규칙을 문서 자신에게 먼저 적용한다. After 예시 회귀가 가장 흔한 실패다. / README maintenance principle — apply each rule to this document itself first; regressing After examples is the most common failure.

## [0.9.0] - 2026-07-06

생성 모드 도입, 3중 반복 구조 통합, 채점표를 fail 조건으로 교체, eval 확장. / Generation mode; consolidated triple-redundant structure; replaced scoring rubric with fail conditions; expanded evals.

- **추가/Added** 생성 모드 — 한국어 산문을 새로 쓸 때도 발동해 slop을 애초에 만들지 않는다. slop이 태어나는 순간은 교정 요청이 아니라 생성 요청이다. / Generation mode — the skill now triggers on requests to write new Korean prose, preventing slop at the source instead of only cleaning it up afterward.
- **추가/Added** 긴 글 교정 순서 — 구조 slop(서론·결론·반복 문단) → 문단별 표현 slop → 전체 리듬. 문단 대응 유지, 전면 재작성 금지. / Long-text editing order — structural slop first, then per-paragraph phrasing, then overall rhythm; keep paragraph correspondence, no full rewrites.
- **추가/Added** 레지스터 표 3종 확장 — 이메일·공지, 마케팅 카피·SNS, 기술 문서. / Three new registers — email/notice, marketing copy/SNS, technical docs.
- **변경/Changed** 채점표(49/70) 삭제, "출력 전 필수 점검" fail 조건 5개로 교체 — LLM 자가 채점은 항상 후하게 나와 행동을 바꾸지 못한다. 검증 가능한 fail 조건(날조·길이 절반 이하·리듬 획일화·레지스터 이탈·마커 잔존)만 남김. / Removed the 49/70 scoring rubric in favor of five verifiable pre-output fail conditions — LLM self-scoring is reliably generous and changes nothing; checkable fail conditions do.
- **변경/Changed** 빠른 체크리스트 삭제 — 핵심 규칙·상세 패턴과 3중 중복으로 동기화 비용만 발생. 핵심 규칙 11개가 빠른 스캔 층, 상세 패턴이 단일 정본. / Removed the quick checklist — it triplicated the rules and detail patterns, costing sync effort. The 11 core rules are the scan layer; detail patterns are the single source of truth.
- **변경/Changed** description 재설계 — 과발동 위험 키워드("어색하다", "딱딱하다" 단독) 제거, 사문화된 패턴-인용 시나리오를 (1)에 통합, 생성 시나리오 (3) 추가, 제외에 "단순 어조 변경" 명시. / Redesigned description — dropped overfiring standalone keywords, merged the dead pattern-quoting scenario, added the generation scenario, excluded plain tone changes.
- **수정/Fixed** `evals/evals.json` JSON 문법 오류(배열 미종결, 후행 쉼표)로 파일 전체가 파싱 불가였던 문제. / Fixed invalid JSON in `evals/evals.json` (unterminated array, trailing comma) that made the file unparseable.
- **추가/Added** eval 3케이스 — 줄표·대조 연쇄, 불릿 의존(이메일 레지스터), 생성 모드. 트리거 eval에 퇴고·윤문·생성 요청 케이스 추가, cover letter 케이스는 생성 모드 도입으로 true로 전환. / Three new eval cases (em-dash/stacked antithesis, bullet dependence, generation mode); new trigger cases for 퇴고/윤문/generation; the cover-letter case flips to true under generation mode.

## [0.8.0] - 2026-07-06

실사용 관찰 기반 패턴 추가, 작업 절차·출력 형식 명시, 표기 정리. / New patterns from real-world usage observations; explicit workflow/output format; notation cleanup.

- **추가/Added** "작업 절차와 출력 형식" 섹션 — 교정문 전문 먼저, 주요 변경 3~5개 한 줄씩, slop 없으면 고치지 않는다고 답하기. 발동 후 행동이 미정의였던 공백 해소. / New "workflow and output format" section — corrected text first, 3–5 one-line change notes, decline to edit when the source has little slop. Fills the gap where post-trigger behavior was undefined.

- **추가/Added** 줄표(—) 남용 패턴 — 영어 em dash 문체의 직수입, 문단당 1개 이하 기준. / Em-dash overuse pattern — imported from English LLM style; at most one per paragraph.
- **추가/Added** 불릿 나열 의존 패턴 — 서술 문단이 뼈대, 불릿·표는 보조. / Bullet-list dependence pattern — prose paragraphs as the skeleton, bullets/tables as support.
- **변경/Changed** 이분법 대조 규칙 확대 — "단순히" 없는 일반형 `X가 아니라 Y다`와 대조문 연쇄(2회 이상 반복) 금지 명시. / Extended the false-dichotomy rule to the plain "not X but Y" form and to stacked contrastive sentences.
- **변경/Changed** 동어반복 부연에 문단 단위 기준 추가 — 새 정보 없는 문단은 삭제 후보. / Restatement rule now applies at paragraph level — paragraphs adding no new information are deletion candidates.
- **변경/Changed** description 트리거에 "윤문", "퇴고", "리라이팅", "매끄럽게" 키워드 추가. / Added "윤문/퇴고/리라이팅/매끄럽게" (polish/rewrite) keywords to the trigger description.
- **수정/Fixed** 표기 정리 — 수사적 질문 예시의 깨진 백틱, "예 :" 띄어쓰기 불일치, 끊긴 문장("핵심 규칙은 slop을 다룬다"), 줄표 규칙 설명문이 스스로 줄표를 쓰던 자기모순. / Notation cleanup — broken backtick in the rhetorical-question example, inconsistent "예 :" spacing, a dangling sentence, and the em-dash rule ironically using an em dash itself.

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
