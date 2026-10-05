# Final Adjudication

## Identity / evidence chain

- Source / frozen baseline / Bible paths, versions and SHA-256：[填写]
- Frozen Coverage / Findings / Summary / Cross-check locations and digests：[填写]
- Evidence Manifest / corrections / ERRATA references：[填写；无则说明]
- Decision date / ADJUDICATION_AGENT：[填写]
- FINAL_AUTHORITY authorization and scope：[填写；不得由G3自授权]

本阶段只裁决，不改译稿。Decision只允许ACCEPT / MODIFY / REJECT / INVALIDATED / EDITORIAL_ONLY / PRE_FIXED。

## Finding [ID] / Adjudication [ID]

| Field | Value |
|---|---|
| Finding / related internal IDs | [填写] |
| Evidence status | [六维逐项PASS/FAIL/未核验及理由；附audit定位] |
| Verified source quote / location | [真实source及版本] |
| Verified translation quote / location | [冻结baseline及版本] |
| Context and evidence correction | [填写；错误引文关联ERRATA] |
| Decision | [允许值选一] |
| Final severity | [BLOCKING / MAJOR / MINOR / STYLE；无成立缺陷可N/A] |
| Root cause | [填写] |
| Affected scope | [精确位置/完整白名单及排除项；必要时链接Occurrence Map] |
| Canonical wording / rule | [最终拟实施文本/规则；非修订项写保留措施] |
| Automatic replacement allowed? | [默认NO；YES仅说明已核准白名单、断言与边界] |
| Manual verification required? | [逐项要求；自动执行不免除source/entity核验] |
| Regression requirement | [Finding closure及相邻/实体/术语/结构保护] |
| Rationale | [证据如何支持决定，不以投票替代] |
| SOURCE disposition / evidence limitation | [KEEP_LITERAL或NOTE_CANDIDATE，仅适用时填写；不授权加注] |

## Closed revision set

| Change proposal ID | Adjudication ID | ACCEPT / MODIFY | Unit / exact scope | Before → After / rule | Exclusions | Regression |
|---|---|---|---|---|---|---|
| [填写] | [填写] | [选一] | [填写] | [填写] | [填写] | [填写] |

- Authorized body occurrence count：[填写]
- Authorized Bible-only rule count（独立口径）：[填写]
- PRE_FIXED protections / REJECT / INVALIDATED exclusions：[填写]
- EDITORIAL_ONLY / SOURCE notes（不进入正文change set）：[填写]
- Occurrence Map required? / rationale / unresolved entities：[填写]
- Unresolved BLOCKING / MAJOR translation or process issues：[填写]

## G3

- Evidence checklist / actual files read：[填写]
- Gate：**[READY FOR REVISION / NOT READY FOR REVISION，选一]**
- Reason / blockers：[填写]
- Authorized next action：[仅最终获准清单；若未授权则STOP]

MUST NOT把待审模板当作PASS。只有ACCEPT/MODIFY可产生修订；SOURCE候选、PRE_FIXED和已失效建议不得混入Applied。
