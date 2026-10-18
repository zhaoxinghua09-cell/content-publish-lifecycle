# AGENTS.md — 给 AI Agent 的工作指引

本文件面向自动化 AI Agent（编码助手、技能加载器、发布流水线机器人）。人类读者请看 [README.md](README.md)。

## 这个仓库是什么

`content-publish-lifecycle` 是一个**内容发布流水线技能包**：把 设计→落地→检查→验证→发布→沉淀 固化为可复用流程。它带两个本地脚本——`publish_attest.py`（零网络算 SHA256 与包级指纹，写 ATTESTATION.md）与 `gen_skill_security_radar.py`（由 `security_results.json` 确定性渲染安全雷达 SVG）。非医疗器械、非医疗软件。

## 可用的工作命令

```bash
# 本地零网络生成权属证明（逐文件 SHA256 + 包级指纹）
python publish_attest.py

# 由结果数据确定性渲染安全雷达 SVG
python gen_skill_security_radar.py --results security_results.json
```

前置依赖：Python 3。无第三方包；两个脚本均不发起网络请求。

## 约定（Do）

- 改动发布件后，重新跑 `python publish_attest.py` 更新 `ATTESTATION.md` 指纹。
- 改 `security_results.json` 后重跑雷达脚本，保持 `security-radar.svg` 与数据一致。
- 任何对外主张须能回溯到源文件与实测数据。

## 禁止（Don't）

- 不要改动 README 顶部「许可说明 · License Notice」与「署名与许可」中的权属字段（© SynomosAI / MIT / 指纹）。
- 不要在雷达图或权属证明中引入随机量或时间戳——它们须可复现、可审计。
- 不要在仓内提交任何密钥、令牌或真实业务数据。
- 不要声称本仓「已认证 / 已商用交付 / 已服务特定客户」；非医疗器械、无临床声明。

## 边界

本仓提供发布流程方法论与本地证明脚本；不绑定任何特定平台或厂商（厂商中立）。具体逐步操作教程随版本迭代补全。
