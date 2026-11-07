---
name: edu-recruitment-management-agent-core
display_name: '招聘流程管理核心助手'
display_name_en: 'Recruitment Management Agent Core Assistant'
description: '为招聘流程管理提供输入校验、结构化整理和成果模板支持'
description_zh: '校验岗位需求、招聘漏斗、渠道、面试安排、候选人阶段和团队分工的完整性，并整理为可交付结构'
description_en: 'Validate structured inputs and prepare an output-ready structure for the parent agent.'
examples_zh:
  - '检查我提交的输入字段是否完整'
  - '整理这份业务资料并标出冲突项'
examples_en:
  - 'Check whether my structured input is complete.'
  - 'Organize the supplied business information and flag conflicts.'
version: 1.0.1
author: '广州金励泽科技服务有限公司'
---

# 招聘流程管理核心助手

本Skill是Agent内部的结构化支持组件，不替代Agent的诊断、方案设计、人工确认和复盘职责。

## 产品契约

- 核心任务：招聘全流程管理。
- 主要风险：保存候选人敏感信息或自动淘汰缺少依据
- 去重边界：与MT-CRM区分招聘候选人流程，不管理销售线索；与单次招聘计划相比包含多阶段协同。

## 输入

- 岗位需求
- 招聘漏斗
- 渠道
- 面试安排
- 候选人阶段和团队分工

## 工作流程

1. 用户提供结构化JSON时，先执行 @scripts/validate_input.js。
2. 输入缺失时返回缺失字段，不要求Agent自行编造。
3. 输入冲突时返回确认项，暂停正式结论。
4. 安全检查通过后，按 @templates/OUTPUT_TEMPLATE.md 建立空结构。
5. 将结构交回Agent继续专业处理。

## 专属检查

- 从岗位任务、汇报关系、任职资格、协作接口和绩效证据出发，不针对个人画像。
- 区分必要条件与可培养条件，避免歧视性、无限扩张或不相关限制。
- 涉及劳动关系、纪律、薪酬和合规结论时要求专业人员复核。
- 招聘、培训、绩效和入职材料应保留责任人、时间与确认节点。

## 边界

不得提供正式法律意见，不得进行无依据淘汰或采集与岗位无关的个人信息。

本Skill不产生最终业务结论，不调用外部收费API，不保存用户数据。
