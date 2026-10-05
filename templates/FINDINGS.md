# Findings

被引用artifact的身份填写规则（说明，不是本文件自身份字段）：持久路径/资源ID；版本/revision；精确字节可用时MUST记SHA-256，否则记provider身份、稳定revision及准确版本重开定位；导出文件另记格式、来源revision和SHA-256。

## Review identity

- Role / review date / scope：[填写]
- Source artifact identity：[填写]
- Translation baseline artifact identity：[填写]
- Bible artifact identity：[填写]
- Isolation statement / supplied materials（independent review必填）：[填写]
- Coverage and Summary artifact identities：[填写]
- Freeze date / artifact identity register：[填写]

只允许Severity＝BLOCKING / MAJOR / MINOR / STYLE；Type＝TRANSLATION / SOURCE / PROCESS / EDITORIAL_NOTE。

## Finding [stable ID]

复制本节用于每一项；不得用零Finding掩盖未覆盖范围。

| Field | Value |
|---|---|
| Finding ID | [填写] |
| Severity | [从允许值选一] |
| Type | [从允许值选一] |
| Unit | [稳定单元ID] |
| Source location | [页码体系或版本内锚点/段落位置] |
| Source quote | [从真实source读取的逐字引文；不得凭记忆或外部事实重建] |
| Translation location | [冻结baseline位置] |
| Current translation | [冻结baseline实际文本] |
| Context | [相邻动作、对象、限定词、指称] |
| Issue | [可证实的含义/规则缺陷；偏好不是Finding] |
| Root cause | [译文、作者疑点或流程原因及支持证据] |
| Affected scope | [已知单处/全局候选范围及不确定性] |
| Suggested direction | [建议，不是执行授权] |
| Confidence | [程度及理由] |
| Evidence basis | [实际读过的文件/位置；外部依据与source原文分开] |
| Status | [review记录当前进度/待核验内容；最终Decision在裁决中记录] |

PROCESS的Source quote不适用时写N/A并给出实际流程/制品证据。所有待修订项仍需六维重新核验。冻结后发现错误MUST用独立ERRATA/纠正材料关联本ID，不回写引文或悄悄删行。
