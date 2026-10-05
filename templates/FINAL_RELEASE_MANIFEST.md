# Final Release Manifest

模板使用：所有字段填写实测值；不适用须说明。MUST先验证artifact实际存在、可读取及最终版本，不能将占位符或生成声明作为PASS。

被引用artifact的身份填写规则（说明，不是本文件自身份字段）：持久路径/资源ID；版本/revision；精确字节可用时MUST记SHA-256，否则记provider身份、稳定revision及准确版本重开定位；导出文件另记格式、来源revision和SHA-256。无直接源字节的原生artifact可将bytes/digest填N/A及理由，不能缺少其稳定provider revision；实际DOCX/PDF/EPUB文件必须记录精确字节摘要。

## A. Release identity

- Project / release version / date / timezone：[填写]
- FINAL_AUTHORITY scope / G4 evidence：[填写]
- Release status：[待验证；最终见G5]

## B. Final SSOT

| Field | Value |
|---|---|
| Absolute path / persistent ID | [填写] |
| Filename / format / version or provider revision | [填写] |
| Provider identity / exact revision reopen locator（原生artifact适用） | [填写] |
| Size in bytes / SHA-256（精确字节可用时必填） | [填写；无可寻址源字节才可N/A，身份按上行记录] |
| Modification timestamp and timezone | [填写] |
| Character count / exact counting convention | [是否含空白、Markdown、元数据、换行归一；不是出版字数] |
| Unit count / expected total / source order | [填写] |

## C. Final deliverables and version binding

| Format / filename | Path / persistent ID | Bytes / SHA-256（字节制品必填） | Version/revision identity / exact reopen locator | Modified timestamp（适用时） | Pages or applicable structural count |
|---|---|---|---|---|---|
| [填写] | [填写] | [填写] | [填写] | [填写] | [固定页数或EPUB spine等口径] |

- Revision state绑定：SSOT、单元源、Bible、deliverables与QA各自可复现身份关联：[填写]
- Export identity（有导出时）：导出格式、来源provider revision、导出精确字节SHA-256：[填写；无导出则N/A]
- 跨格式内容传递证据（单元/段落/数字/结构/脚注等）：[填写；相同生成日期/文件名或分别有hash不够]
- 字节制品仅复制/改名：旧路径、新路径、相同SHA-256及实际字节相等确认：[填写；否则N/A]。原生制品改名后的provider revision身份关联：[适用时填写]
- 实际打开/解析/渲染方法与结果：[填写；未启动阅读器不得声称已在该阅读器测试]

## D. Bible version

- Bible artifact identity / applicable modification timestamp：[填写]
- Approved rule updates / adjudication references / count：[填写]
- Frozen review Bible preserved at：[填写]

## E. QA evidence

| Artifact | Actual path / persistent ID | Reproducible identity（字节摘要或provider/revision/重开定位） | Proves |
|---|---|---|---|
| Revision Change Log | [填写] | [填写] | 获准清单与实施闭合 |
| Post-revision QA | [填写] | [填写] | 回归、差异守卫及制品检查 |
| Final Adjudication / evidence audit | [填写] | [填写] | 裁决与六维证据 |
| Entity / PRE_FIXED regression（适用时） | [填写] | [填写] | 精确身份及既有修复保护 |
| Structural / document / visual evidence | [填写] | [填写] | 实际制品而非计划版本 |

结构检查 MUST覆盖范围内单元、目录、卷首/书后内容、表、图、caption、footnote、特殊字符及乱码；不存在的对象填N/A及实际对象数，不笼统声称“全部正常”。Index及其它范围例外：[填写既定决定与证据]

Visual QA：required? [填写理由]；evidence directory/artifact [填写]；total [填写]；pages/views reviewed [填写]；missing [填写]；rendering failures [填写]；blocking layout defects [填写]；cosmetic notes [填写，不自动修改]。

方法：实际新目视范围 [填写]；如继承同图证据，旧检查记录、逐页相同hash及当前制品绑定 [填写]；reflow格式需说明阅读器/视口及覆盖，不能虚构固定分页或声称未做过的检查。

## F. Revision statistics

| Measure | Result / evidence |
|---|---|
| Authorized / Applied / Verified PASS body changes | [填写，三者须相等] |
| Bible-only rules（独立计数） | [填写] |
| Unexpected substantive diff / other unexplained diff | [填写，必须均为0] |
| Finding closure and terminology regression | [填写] |
| Entity resolved / wrong-entity / unresolved | [填写，后两者须为0；不适用说明] |
| No blind replacement side effects | [证据] |
| PRE_FIXED / REJECT / INVALIDATED guards | [证据] |
| Coverage and applicable visual QA | [填写] |

计数定义与范围：[填写；Finding数、编辑命中数、段落数及Bible规则数不得混算]

## G. Frozen inputs

| Artifact | Path / persistent ID | Frozen identity（字节摘要或准确provider revision） | Verified identity（同口径） | Result |
|---|---|---|---|---|
| Original Source | [填写] | [填写] | [填写] | [填写] |
| PRE translation baseline / review Bible | [填写] | [填写] | [填写] | [填写] |
| Coverage / Findings / Summary / Cross-check | [逐文件填写] | [填写] | [填写] | [填写] |
| ERRATA / audit / occurrence map（适用时） | [逐文件填写] | [填写] | [填写] | [填写] |

若存在历史Manifest drift，引用修正材料；字节制品保留SUPERSEDED DIGESTS和CURRENT AUTHORITATIVE DIGESTS，原生制品保留superseded/current authoritative revision identities；不得抹去旧值或把失效Finding恢复为有效。

## H. Known editorial notes

| Existing Finding / decision | SOURCE disposition | Evidence limitation / retained wording rationale | Future scope boundary |
|---|---|---|---|
| [填写；无则说明] | [KEEP_LITERAL / NOTE_CANDIDATE] | [填写，不伪称外部事实已核实] | [候选不等于新注释授权] |

仅沿用已裁决的SOURCE/editorial notes；不新增事实核查或正文修订。

## I. G5 final status

- SSOT / deliverables / Bible version-bound：[证据]
- Authorized change closure / diff guard：[证据]
- Reviewer-error、entity与PRE_FIXED保护：[证据]
- Structural / document / applicable visual QA：[证据]
- Frozen evidence intact / Manifest materialized：[证据]
- Blockers：[必须为0才可PASS]
- **[FINAL RELEASE QA PASS / FINAL RELEASE QA FAIL，选一]**
- Final SSOT / deliverables / Manifest actual paths：[填写]

STOP。Publication Enhancement、索引重建、新注释与文学重写不属于本次release。
