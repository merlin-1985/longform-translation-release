# Revision Change Log

## Version and scope

- G3 adjudication path / version / SHA-256：[填写]
- FINAL_AUTHORITY authorization reference：[填写]
- PRE snapshots / baseline / Bible versions and hashes：[填写]
- POST SSOT / unit sources / Bible versions and hashes：[填写]
- Final deliverables / content-transfer evidence：[填写]
- Execution date / REVISION_AGENT：[填写]

## Authorized changes

| Change ID | Finding / Adjudication ID | Unit | Location / occurrence ID | Before | After | Reason | Execution method | Regression result / evidence |
|---|---|---|---|---|---|---|---|---|
| [填写] | [填写] | [填写] | [版本内坐标和上下文] | [真实旧文本] | [获准新文本] | [填写] | [定点/已核准白名单；旧文本断言] | [PASS/FAIL/未检；证据位置] |

另列Bible-only规则更新，字段同上，但Unit标明Bible；不计入正文命中数。Before/After很长时可引用实际落盘的完整段落记录，不能仅写“已修改”。执行前版本/旧文本不匹配则STOP。

## Closure and regression

| Measure | Authorized | Applied | Verified PASS | FAIL / unresolved | Evidence |
|---|---|---|---|---|---|
| Body edit occurrences | [填写] | [填写] | [填写] | [填写] | [填写] |
| Bible-only rules | [填写] | [填写] | [填写] | [填写] | [填写] |
| PRE_FIXED protections（非新增编辑） | [适用数] | N/A | [填写] | [填写] | [填写] |

计数口径/一个Finding对应多个occurrence/首次释名等额外获准编辑：[填写；不为凑数重分类]

| Regression | Result | Evidence / version |
|---|---|---|
| Finding closure | [填写] | [填写] |
| Terminology / entity regression and exclusions | [填写] | [填写] |
| PRE_FIXED / REJECT / INVALIDATED protection | [填写] | [填写] |
| SOURCE unchanged except separately authorized translation edits | [填写] | [填写] |
| Structural / document QA / applicable visual QA | [填写] | [填写] |
| Frozen input hashes unchanged | [填写] | [填写] |

## PRE vs POST diff guard

- Authorized content changes及对应Change IDs：[填写]
- Expected formatting changes及原因、验证：[填写]
- Unexpected substantive diff count：[实测；必须为0才可PASS]
- Any other unexplained diff / resolution：[填写；不得以格式变化掩盖内容修改]
- Comparison method, inputs and evidence location：[填写；文本差异与二进制hash各司其职]
- Post-revision QA artifact / SHA-256：[填写]
- G4：**[POST-REVISION QA PASS / FAIL，选一]**

若QA结果更新改变本日志/清单的字节摘要，保留执行时版本及后续版本关联；不得让旧回归证据假装绑定新版文件。
