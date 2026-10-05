# Release Gates

只有G1–G5是Major Gates。checkpoint使用工作记录，不创设新Gate。每次判定MUST记录日期、责任角色、输入/输出版本、PASS/FAIL、证据位置及blocker。所有必需artifact适用SKILL.md的Materialization Rule。

## G1 — TRANSLATION BASELINE FROZEN

- **Required evidence：** 权威源件版本/hash；单元与范围清单；Bible版本；完整译稿；内部QA和已修复项记录；冻结baseline实际文件与hash。
- **PASS conditions：** 范围内单元全部交付且书序正确；数字、引语、结构及提取异常已检查；索引/图片等范围例外明确；内部QA无阻断冻结的未决缺陷；合并baseline与单元稿对应，源件和baseline均保留。
- **FAIL conditions：** 缺单元/可译内容、无法辨认的源内容被猜补、Bible冲突影响理解、合并稿版本不明或只有生成声明。
- **Allowed next action：** 准备隔离review包，开始独立审校；不能把内部QA PASS当作最终release。
- **Mandatory STOP behavior：** FAIL停止独立审校准入，处理具体冻结阻塞；冻结后若需改baseline，另建版本并明确受影响review，不覆盖旧版。

## G2 — INDEPENDENT REVIEW COMPLETE

- **Required evidence：** G1输入摘要；隔离声明；实际Coverage、Findings、Summary及各自当前摘要；任何缺口/排除项说明。
- **PASS conditions：** INDEPENDENT_REVIEWER未读取内部QA结论；覆盖全部约定范围；输出可读且已落盘冻结；发现数量和覆盖记录自洽。Finding可以尚未裁决，G2不是确认其正确。
- **FAIL conditions：** 审查被内部结论污染、只审部分却称全覆盖、没有明确baseline、文件未落盘/无法读取。
- **Allowed next action：** 开放内部QA，Cross-check并冻结结果；开展Evidence Integrity Audit及Adjudication。
- **Mandatory STOP behavior：** FAIL不进入正式交叉核对或宣称独立review完成；恢复隔离/覆盖后重验。禁止以多数review结论直接修订。

## G3 — READY FOR REVISION

- **Required evidence：** G2冻结包、Cross-check、当前证据Manifest与纠正材料；六维Evidence audit；最终裁决；闭合change set；必要Occurrence Map；相应FINAL_AUTHORITY授权记录。
- **PASS conditions：** 每项Finding都有可追踪处置；所有拟改项六维核验完成；source-quote mismatch与digest drift已解决；无未决BLOCKING/MAJOR译文或流程问题；范围、排除项、规则与回归明确；实体未决为0；只有ACCEPT/MODIFY进入清单。
- **FAIL conditions：** 真实源文未核对、引用错误仍作为依据、版本权威不明、身份或全局范围不清、裁决前已改稿且无可靠PRE可恢复，或修订授权缺失。
- **Allowed next action：** 仅实施获准closed change set。授权已在此前覆盖本范围则继续，不重复确认。零修订清单可进入记录为0的日志及回归阶段。
- **Mandatory STOP behavior：** FAIL记录`NOT READY FOR REVISION`，禁止改稿。G3只表示准入，不扩展授权。已处置SOURCE候选的外证缺口可以保留为编辑限制，不得转成静默修订或伪称已证事实。

## G4 — POST-REVISION QA PASS

- **Required evidence：** G3裁决及授权；PRE快照；POST单元/SSOT；逐项Revision log；实际新deliverable；Post-revision QA及版本绑定。
- **PASS conditions：**
  - Authorized＝Applied＝Verified PASS；正文命中、Bible-only规则、PRE_FIXED分列，不以重分类凑数。
  - Finding closure、术语回归、entity回归、PRE_FIXED保护全通过；REJECT/INVALIDATED目标未误改；SOURCE无静默纠正。
  - PRE vs POST diff逐项可归入获准内容修改或解释明确的必要格式变化；unexpected substantive diff＝0，未解释差异＝0。
  - 全部单元、目录、章节、表/图/说明、脚注、特殊字符和范围例外正确；Final SSOT与实际制品内容对应。
  - 文档可解析/打开；必要时实际渲染检查。固定版式交付或布局可能受影响时 MUST有全页视觉证据，不能只看文本或抽样即称全覆盖。重排EPUB按内容/spine/导航及已声明的阅读器/视口检查，不虚构固定页数。
  - 冻结输入未变；QA证据绑定的是最终待交付版本。
- **FAIL conditions：** 缺修订/误替换、PRE_FIXED回退、越界润色、制品内容不对应、格式故障、必要视觉证据缺失或版本未绑定。
- **Allowed next action：** 冻结当前成果，进入Release Closeout；不得继续优化译文。
- **Mandatory STOP behavior：** FAIL停止closeout。清单内实施错误可按原授权修复并重验；新正文需求须回到裁决/授权，不能借回归扩大范围。

视觉证据 MUST说明总数、实际检查范围、缺失页、渲染失败和阻断布局缺陷。可复用先前真正检查过且PNG字节/hash完全相同的页面证据，但必须绑定旧检查、当前制品与每页hash；变化页全部重新检查，不把同图继承称为重新目视。

## G5 — FINAL RELEASE QA PASS

- **Required evidence：** G4最终状态；Final SSOT；Final deliverable(s)；Bible；Revision log；Post-revision QA；完整Final Release Manifest；冻结输入校验。
- **PASS conditions：**
  - SSOT及每个实际制品有明确绝对路径/持久ID、文件名、字节数、SHA-256、修改时间、版本；单元数及字符统计口径明确；页数适用则登记，不适用须说明。
  - MD/其它SSOT、制品、Bible与QA处于同一revision state。hash只证明文件身份，必须另有单元/段落/结构或等价内容传递证据证明跨格式对应。
  - 获准清单闭合、unexpected substantive diff＝0；已失效reviewer建议、entity和PRE_FIXED保护仍PASS；全部必需文档/视觉QA证据齐全。
  - frozen evidence和原件摘要不变；editorial notes如实保留；Manifest本身已落盘可读，无未填字段被当成PASS。
- **FAIL conditions：** 找不到实际最终制品、记录绑定旧版、仅文件名显示Final却无证据、制品在QA后变更未重验、正文或冻结审校材料被覆盖、任何发布阻塞未解决。
- **Allowed next action：** 仅交付Final SSOT、final deliverables及Manifest路径与状态。文件名无须包含Final；若仅复制/改名，验证字节相等并登记旧/新路径与同一hash，不重新生成正文。
- **Mandatory STOP behavior：** FAIL输出`FINAL RELEASE QA FAIL`和具体blocker；PASS输出`FINAL RELEASE QA PASS`后STOP。不自动继续Publication Enhancement、索引重建或新注释。
