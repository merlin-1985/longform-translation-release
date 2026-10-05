---
name: longform_translation_release
description: Use when translating or releasing a book, technical document, research report, or other long PDF, DOCX, or EPUB that requires independent review and an auditable translation release; also when resuming such a project at a recorded lifecycle stage.
---

# Longform Translation Release

PUBLIC DRAFT CANDIDATE v0.1。将长篇翻译交付为可审计、可裁决、可回归的工程结果。MUST表示必须；MUST NOT表示禁止；SHOULD表示有理由才可偏离。

## 适用与边界

- 用于完整长篇项目或其已授权阶段；单段即时翻译通常不需要本流程。
- MUST先确认源件、目标语言/locale、读者、输出格式、完整范围及现有授权；已有明确答案不得重复询问。
- 恢复项目时 MUST验证已有证据并从最早未满足的checkpoint继续，不重复翻译已冻结内容。
- 不自动执行Publication Enhancement、版式重设计、索引重建、新增注释、新事实核查专项或文学重写。G5后STOP。
- v0.1只有流程、政策与模板；不包含自动化代码、固定平台依赖或特定模型要求。格式提取、OCR、渲染与hash使用环境中适用的现有能力；不可用时如实报告限制。

## Roles

| Role | 责任与权限 |
|---|---|
| FINAL_AUTHORITY | 确认范围、授权、重大证据版本争议及最终交付；Agent不得自行扮演这一授权来源 |
| PRIMARY_TRANSLATOR | 冻结源件、制定Bible、按单元翻译与合并；并行时分配互不冲突的单元，统一合并Bible |
| INTERNAL_QA_AGENT | 源译自检、完整性和一致性检查，记录内部发现及已修复项 |
| INDEPENDENT_REVIEWER | 在隔离上下文中审查冻结源译对，不读取内部QA结论；只产出review证据 |
| ADJUDICATION_AGENT | G2后交叉核对、证据审计、逐项裁决与界定变更范围；不改译稿 |
| REVISION_AGENT | 只实施获准清单，记录差异、组织回归及发布收口 |

同一Agent可承担多个角色，但独立审校 MUST与内部QA信息隔离；需新上下文或可证明的隔离，不能靠“忽略先前结论”模拟。执行回归 SHOULD与实施修订分开复核；不增加强制角色。并行只用于独立单元，MUST指定所有权、输入版本与合并责任，不并发改共享Bible/SSOT。

## Evidence hierarchy / 七条硬规则

**Original Source > Frozen Translation Baseline > Translation Bible > Reviewer Evidence > Agent Judgment**。此顺序决定证据冲突时的优先级；基线记录“审查了什么”，不意味着基线不可能有错。

1. **Source is Authority。** MUST直接核对真实源件；提取文本/OCR是派生材料，不能推翻源件。
2. **Review Finding ≠ Truth。** 进入修订清单前 MUST重新验证source quote、translation quote、location、context、root cause、scope；允许INVALIDATED，投票与信心不能替代证据。
3. **SOURCE ≠ TRANSLATION。** 作者事实/数字/技术/时序疑点不能静默纠正为外部事实；译文不忠实才属于TRANSLATION。
4. **Frozen evidence不可静默改写。** 独立review的Coverage、Findings、Summary完成时冻结；后续Cross-check完成时同样冻结。reviewer error用ERRATA或等价追加纠正材料记录，历史原件保留。
5. **Adjudication与Revision分离。** 裁决正文候选只产生ACCEPT / MODIFY / REJECT / INVALIDATED；PRE_FIXED、EDITORIAL_ONLY是非修订处置。只有G3 PASS且已有FINAL_AUTHORITY相应授权才可实施；G3本身不授予权限，不重复索取已覆盖范围的授权。
6. **不得默认blind global replace。** 人名、专名、术语、缩写、多义词或entity-name collision MUST评估Occurrence Map需求；指称不明则STOP相关变更，不能批量猜替。
7. **Release必须可证明。** MUST具备Final SSOT、实际deliverable、Revision log、Post-revision QA、Manifest及version/hash binding，且unexpected substantive diff＝0；“已检查”不是证据。

## Lifecycle / Stage execution contract

按书序/文档逻辑顺序建立稳定单元ID；数量来自实际范围，不预设页数、章节数或修改数。以下checkpoint不构成额外正式Gate。

| Stage | INPUT | EXECUTION | OUTPUT / EVIDENCE | GATE | STOP CONDITION |
|---|---|---|---|---|---|
| Source Freeze | 原件、范围和格式要求 | 确认权威版本；读取能力/抽取异常检查；建立单元与定位方案；保存原字节 | 源件登记：路径、大小、版本、SHA-256、单元清单及范围例外 | checkpoint | 源件不可读、版本未定、不可恢复缺页/提取内容 |
| Translation Bible | 已冻结源件、读者/locale | 约定声音、术语及结构处理，明确例外；不猜专名事实 | Bible初版及负责合并者 | checkpoint | 影响全局含义的规则冲突未解决 |
| Primary Translation | 源件、Bible、分配单元 | 逐单元忠实翻译；保留数字、引语、对象关系和结构；按书序合并 | 单元稿、覆盖记录、术语提案 | checkpoint | 源内容不可辨认、单元缺失；禁止补造 |
| Internal QA | 全部单元稿与原件 | 源译核对、全局一致性和结构检查；记录修复；冻结审校基线与Bible版本 | 内部QA、PRE_FIXED证据、冻结baseline、版本登记 | **G1** | 完整性或基线绑定失败 |
| Independent Review | 隔离包：源件、baseline、Bible和中性范围说明 | 不读取内部QA；核对全部约定范围；记录发现、未覆盖内容和方法 | Coverage、Findings、Summary；隔离声明与输入摘要 | **G2** | 信息隔离失败、覆盖缺口、声称完成但文件未落盘 |
| Cross-check | G2冻结包、内部QA | 此时才开放双方记录；按根因/位置对齐，保留分歧和PRE_FIXED | 冻结Cross-check及稳定ID关联 | checkpoint | 重复计数、基线不同且不能定位对应关系 |
| Evidence Integrity Audit | 源件、baseline、Bible、review、纠正材料 | 逐项核验六维证据；处理quote mismatch、digest drift；审计替换范围 | Evidence audit；必要的ERRATA、Manifest correction、Occurrence Map | checkpoint | 证据不可读取、权威版本不明、实体身份未决 |
| Adjudication | 已核验证据、Cross-check | 用裁决模板界定每项范围、规则、排除项及回归要求；不改译稿 | 最终裁决与closed change set、非正文处置记录 | **G3** | 未决BLOCKING/MAJOR译文或流程问题；范围/授权未定 |
| Controlled Revision | G3、获准清单、PRE快照 | 仅ACCEPT/MODIFY定点实施；Bible规则更新须单列授权；记录每次Before/After | POST稿、新SSOT、Revision log、PRE vs POST差异 | checkpoint | 旧文本/位置/版本不匹配、越界变更、清单外修改需求 |
| Regression QA | PRE/POST、裁决、日志、新deliverable | 发现闭合、术语、实体、PRE_FIXED、结构、文档与差异守卫；必要时逐页视觉QA | Post-revision QA、最终制品检查与版本绑定 | **G4** | 获准项未闭合、回归失败、未授权实质差异或文档故障 |
| Release Closeout | G4实际制品与证据 | 冻结当前结果；重读制品和摘要，完成Manifest；不润色或重新构建内容 | Final SSOT、final deliverables、Final Release Manifest | **G5** | 任一必需制品/绑定/完整性证据失败；PASS后也STOP |

## Major Gates / Stop rules

正式Gate只有五个：[RELEASE_GATES.md](references/RELEASE_GATES.md)是详细准入标准，过Gate前 MUST读取对应节。

| Gate | 唯一成功状态 |
|---|---|
| G1 | TRANSLATION BASELINE FROZEN |
| G2 | INDEPENDENT REVIEW COMPLETE |
| G3 | READY FOR REVISION |
| G4 | POST-REVISION QA PASS |
| G5 | FINAL RELEASE QA PASS |

- FAIL则停止依赖它的下游动作；可继续无依赖的已授权工作。明确blocker、影响及所需证据，不以“完成大部分”放行。
- Artifact Materialization Rule：每个Gate前 MUST确认文件实际存在、明确路径/ID、可读取、当前版本明确、digest/version可绑定；对话中的文件名或“已上传”声明不算落盘。
- Manifest drift MUST按[REVIEW_POLICY.md](references/REVIEW_POLICY.md)保留旧metadata、确认新权威版本并重新绑定；禁止猜旧版本、静默换hash或为hash回滚有效证据。
- G3/G4后证据或内容变化 MUST重新验证受影响Gate及下游绑定；保留旧结果，不伪称旧PASS适用于新版本。
- Closeout若发现BLOCKING artifact failure，仅在授权范围内修复制品并重验受影响证据；若需要正文变更，STOP并退回裁决/授权，不能借发布收口扩写。
- G5输出最终SSOT、最终制品、Manifest实际路径和状态，然后STOP。

## Reference / Template routing

运行记录属于目标翻译项目；MUST NOT回写本Skill模板。允许把Coverage、audit、ERRATA等放进既有报告的清晰独立章节，避免无必要文件膨胀，但冻结记录不得原位重写。

| 时机 | 读取/复制 |
|---|---|
| Review、Cross-check、证据异常、裁决 | [REVIEW_POLICY.md](references/REVIEW_POLICY.md) |
| 任一Gate准入或恢复检查 | [RELEASE_GATES.md](references/RELEASE_GATES.md) |
| 项目规则建立 | [TRANSLATION_BIBLE.md](templates/TRANSLATION_BIBLE.md) |
| 内部或独立review记录 | [FINDINGS.md](templates/FINDINGS.md)；两者保持隔离 |
| 裁决与范围封闭 | [FINAL_ADJUDICATION.md](templates/FINAL_ADJUDICATION.md) |
| 获准修订及回归 | [REVISION_CHANGE_LOG.md](templates/REVISION_CHANGE_LOG.md) |
| 发布收口 | [FINAL_RELEASE_MANIFEST.md](templates/FINAL_RELEASE_MANIFEST.md) |
