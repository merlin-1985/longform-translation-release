# Review Policy

## 1. Independent Review

INDEPENDENT_REVIEWER MUST仅接收权威源件、冻结译文baseline、冻结Bible与中性范围说明。MUST NOT在G2前接收内部QA结论、内部Findings、SOURCE疑点表、PRE_FIXED结果或暗示特定答案的handoff。

输入artifact若夹带内部结论，MUST创建独立审查副本：只剥离结论性元数据，不改源译正文；记录副本与冻结原件的可复现身份及正文等价关系。MUST NOT为了隔离而覆盖原baseline。不能建立隔离则STOP，不能把已受影响的review称为独立；必要时用新上下文重做受影响审查。

review输出必须说明输入的准确已审版本身份、覆盖单元/范围、实际检查方法和未检查项。Coverage总数来自单元清单，检查过的范围不得等同于计划范围。零Finding可以成立，但不是跳过检查的理由。G2前冻结Coverage、Findings和Summary；G2后才开放内部QA做Cross-check，Cross-check完成后冻结。

## 2. Finding model

Severity只能使用以下四种；严重度描述影响，不代表判断已经成立。

| Severity | 定义 |
|---|---|
| BLOCKING | 使当前阶段/交付无法可靠成立：关键源件或单元缺失、制品不可用、证据版本不可确定，或直接阻断任务完成的缺陷 |
| MAJOR | 实质改变核心含义、关键动作、因果、技术含义、数量关系或人物/实体身份；必须在发布前裁决并闭合 |
| MINOR | 局部准确性、遗漏或一致性缺陷，未改变核心叙事/技术关系，但有可证实影响 |
| STYLE | 含义基本正确，但可证明违反已同意的作者声音、读者需求、语言规范或Bible规则；不是个人译法偏好 |

Type只能使用以下四种：

| Type | 定义/边界 |
|---|---|
| TRANSLATION | 译文未忠实表达原文，或违反已批准且不抵触原文的译法规则 |
| SOURCE | 疑点来自原著自身事实、技术、数字、年代、时序或口语概括；忠实译文不是错误 |
| PROCESS | 覆盖、隔离、证据、版本、授权或交付流程缺陷；不能借此自动修改正文 |
| EDITORIAL_NOTE | 非译文缺陷的编辑说明或未来候选处理；不能自动变成新增脚注 |

“另一种译法我更喜欢”不是Finding。每项MUST指出可观察的问题、真实source quote、当前译文、位置、语境、根因和范围。无source quote的流程缺陷可填N/A并提供实际制品证据；不得伪造引文填表。

Confidence是理由充分程度的说明，不是额外severity或证据替代。`Status`只作review记录是否待核验的工作说明，不另建裁决状态机。稳定Finding ID一经冻结不可回收或悄悄改义。

## 3. SOURCE与TRANSLATION

- MUST先判断错误来自哪一层。外部事实与作者不一致，不自动构成译文错误。
- SOURCE采用`EDITORIAL_ONLY`处置，并单列`KEEP_LITERAL`或`NOTE_CANDIDATE`；需要外证作为证据缺口字段记录，不增造正文修订状态。
- NOTE_CANDIDATE只保留候选，不授权新增注释；KEEP_LITERAL不是对作者事实正确性的背书。没有证据支持的SOURCE指控可以REJECT或INVALIDATED。
- 本工作流不自动开展新事实核查专项。外证不足但已确认忠实转译的SOURCE项，可作为已明确处置的编辑备注交付；不得伪称已核实外部真相。若源句本身不能辨认/确定，则仍是内容完整性阻塞。

## 4. Cross-check

G2后按根因、源位置和实际范围关联独立Finding与内部记录。保留双方ID、是否同一缺陷、分歧和既有修复证据。共识不等于正确；内部PASS不否定新证据，reviewer MAJOR也不推翻真实源文。

一个Finding只计一次；分歧/重叠是关系说明，不把标签相加成缺陷总数。已在baseline中正确修复的项记PRE_FIXED，进入回归保护，不重复修订。若只修复一部分，MUST分清已修复范围与仍需裁决的范围。

## 5. Evidence integrity audit

进入修订清单的每一项MUST记录以下六项核验结果：

| 核验项 | 最少证据 |
|---|---|
| source quote | 直接来自当前权威源件的逐字片段及定位；OCR/抽取异常须回看原件 |
| translation quote | 冻结baseline的实际片段与定位，不使用reviewer转述替代 |
| location | PDF物理页与印刷页区分；DOCX用版本内章节/段落/锚点；EPUB用spine/章节/锚点；附上下文帮助定位 |
| context | 前后动作、说话人、技术对象、限定词、指称范围 |
| root cause | 确认是译文问题、原著疑点、流程问题或偏好；指明证据如何支持结论 |
| scope | 精确单处或完整受影响范围；排除项与回归边界 |

Evidence status使用这六项的PASS/FAIL/未核验及具体原因，不扩充裁决枚举。无语义变化的换行/引号归一须注明；改词、补名词或改整句不得伪装成排版归一。

reviewer source-quote mismatch使原论证不可直接用于修订。MUST保留原记录并追加ERRATA，记录Finding ID、错误引文、真实引文、源位置/制品身份、影响与纠正依据。若原指控不成立，INVALIDATED；若真实源译对仍有缺陷，另建清楚关联的核验证据再裁决，不让错误引文继续支持决定。

冻结仅表示版本固定，不表示内容全真。更正不得自动恢复已失效的Finding。Evidence audit和ERRATA可为报告中的独立章节；已冻结报告的纠正必须另存追加材料。

## 6. Reproducible Artifact Identity、materialization与Manifest drift

Every gated artifact MUST have a reproducible identity bound to the exact reviewed version。Gate前MUST实际读取每个必需artifact，并按其类型登记身份：

- Byte-addressable：持久路径/资源ID、适用版本，以及精确字节的SHA-256；同时记录字节数及适用时间。字符/换行归一后的比较另列，不冒充文件摘要。
- Provider-native且无可直接寻址源字节：provider身份、持久资源ID、稳定revision/version ID及重新打开该准确已审版本的定位方式；不要求虚构原生字节hash。仅可变当前链接、修改时间或资源ID不足以绑定版本，无法重开则STOP。
- 后续导出：另记export format、originating provider revision及导出精确字节的SHA-256。导出文件身份和provider-native身份分别保留，并记录对应关系。

远程对象必须确认写入/上传完成并重新读取绑定版本；不能用上传前临时文件或当前可变版本代替已审版本。精确字节可用时SHA-256为MUST，尤其实际DOCX/PDF/EPUB制品；provider-native身份不是免检理由。

报告/Manifest自身的最终identity MUST在完成并冻结后登记于外部既有Gate或交付记录，不回写自身，以免写入自己的SHA-256/revision再次改变其被绑定版本。模板中的身份规则说明适用于被引用artifact，不是自身份待填字段。

Manifest与当前evidence摘要或provider revision身份不符时：

1. STOP依赖该版本的下游动作；查明可获得的创建/上传/修改/导出历史，不猜不存在的旧版本。
2. 记录原因、时间及证据来源；区分实测记录与FINAL_AUTHORITY的说明，不能把时间先后当作内容正确的证明。
3. 保留原Manifest/原值；字节摘要用`SUPERSEDED DIGESTS`、原生版本用superseded identity记录，并标注`STALE / SUPERSEDED METADATA`，不覆写后不留痕。
4. 根据可靠历史和FINAL_AUTHORITY已有明确指定确定authoritative version；权威选择仍有歧义才请求决定。不得为了旧hash回滚当前有效证据。
5. 对正式byte版本重算SHA-256并登记`CURRENT AUTHORITATIVE DIGESTS`；provider-native则登记当前权威revision身份。记录修正原因、授权依据和受影响绑定，重验相关Gate。

仅metadata修正不修改reviewer内容或裁决。若实际内容变更，必须作新证据版本并重验受影响裁决，不能按metadata-only放行。QA状态字段变化也会改变字节摘要或provider revision；保留执行时版本及当前版本关联，不静默更新执行记录。

## 7. Occurrence Map与替换控制

涉及人名、术语、缩写、专名或多义词时，MUST判断同形异义、跨章范围及子串风险。存在entity-name collision或全局范围不清时，MUST建立Occurrence Map；单一确定实例可在裁决中记录不需要map的理由。

Map最少记录：Occurrence ID、baseline版本、单元/位置/上下文、原文entity、当前译法、拟定译法、修改或排除理由、身份是否已确定。扫描完整约定范围，既包括待改项，也包括可能误伤的全名、其它entity与子串排除项。MUST报告扫描总数、待改数、排除数和未决数，互斥计数。

指称未决则STOP相关全局change set。自动执行只允许在已逐项核准的白名单上做版本、位置、旧文本断言；默认Automatic replacement allowed＝NO。MUST保留排除项，并以逐处实体回归和PRE/POST diff证明无blind global replace副作用。

## 8. Adjudication

| Decision | 含义及后续权限 |
|---|---|
| ACCEPT | 问题及具体建议均有证据支持；可进入获准change set |
| MODIFY | 问题成立但需改建议、范围、级别或规则；仅最终明确版本可进入change set |
| REJECT | 已核验后不采纳建议；正文保持，必要时设保护检查 |
| INVALIDATED | 原论证/证据前提失效；不得实施原建议，保留历史及纠正关联 |
| EDITORIAL_ONLY | SOURCE或编辑事项只记录处置；不授权正文/脚注变更 |
| PRE_FIXED | 冻结baseline中已修复且有证据；只加入回归，不计新增Applied |

只有ACCEPT/MODIFY且在授权范围内的具体清单可实施。每项MUST给出final severity、根因、范围、canonical wording/rule、自动替换政策、人工核验要求、回归条件与理由。全局规则不等于无限范围授权；Bible-only规则与正文命中分列计数。无成立缺陷的final severity可填N/A，不能新造severity。
