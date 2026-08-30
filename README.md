# 内容发布全流程（设计→落地→检查→验证→发布→沉淀）· Content Publish Lifecycle

> **方案做完了，怎么变成能发出去的东西？** 把「设计 → 落地 → 检查 → 验证 → 发布 → 沉淀」串成一条可复用发布流水线，让发布从凭感觉变成有据可查。

---

## 一句话定位 · One-line Positioning

方案做完了，怎么变成能发出去的东西？把「设计→落地→检查→验证→发布→沉淀」串成一条可复用发布流水线，让发布从凭感觉变成有据可查。
（*From "design done" to "shipped with evidence": a reusable publish pipeline that turns publishing from guesswork into an auditable process.*）

---

## 痛点与能力 · Pain Points & Capabilities

发布最容易翻车的，不是"写不出"，而是"发出去之前没人查、发出去之后查不到"。本技能把发布拆成六个阶段，每段都有明确产物与检查点：

| 阶段 Stage | 解决什么 What it solves |
|---|---|
| **设计 Design** | 先想清楚"发什么、发到哪、版本号"，把发布目标拆成可执行阶段与检查点，而不是临场发挥。 |
| **落地 Implement** | 按渠道规格把内容适配成可发布形态（标题 / 标签 / 格式 / 长度），产出与源稿解耦的发布件。 |
| **检查 Inspect** | 发布前逐条核对清单（渠道 \| 内容 \| 版本 \| 拟发布时间），任何外发动作**先确认、后执行**。 |
| **验证 Verify** | 本地零网络生成权属证明（ATTESTATION）与安全实测雷达，让"我发的就是我审过的"可核验。 |
| **发布 Publish** | 通过 Git Data API 等受控通道落地到目标仓库 / 渠道，记录链接、时间、状态，形成发布回执。 |
| **沉淀 Consolidate** | 把发布记录、版本、指纹回传归档，支持复盘与版本回溯，下次直接复用流水线。 |

---

## 差异化壁垒 · Differentiators

- **证据链留痕 Evidence-chain logging**：每个发布件带版本号、指纹与回执，全程可追溯。
- **对外主张挂真实依据 Every external claim pinned to real evidence**：结论须能回溯到源文件与实测数据，不凭空宣称。
- **本地零网络权属证明 Local, network-free provenance attestation**：`publish_attest.py` 在本机算 SHA256 与包级指纹，不依赖任何外部服务。
- **安全实测雷达 Security empirical radar**：`gen_skill_security_radar.py` 由 `security_results.json` 确定性渲染雷达图，无随机量、无时间戳污染。

---

## 安装 · Install

通过技能管理器安装：

```bash
openclaw skills install @zhaoxinghua09-cell/content-publish-lifecycle
```

或直接把本仓库中的 **`SKILL.md`** 放入你的 skills 目录即可使用。

---

## 文件清单 · File Manifest

技能包共 9 个文件（包根 8 个 + `references/` 子目录 1 个）：

| # | 文件 File | 说明 Note |
|---|---|---|
| 1 | `SKILL.md` | 技能主说明 / Skill entry |
| 2 | `manifest.json` | 元数据（名称 / 版本 / 作者 / 许可） |
| 3 | `LICENSE.md` | MIT 许可文本 |
| 4 | `references/attestation-template.md` | 权属证明模板 |
| 5 | `publish_attest.py` | 本地权属 / 指纹生成脚本 |
| 6 | `gen_skill_security_radar.py` | 安全实测雷达图生成脚本 |
| 7 | `security_results.json` | 安全实测结果数据 |
| 8 | `security-radar.svg` | 安全实测雷达图 |
| 9 | `ATTESTATION.md` | 权属证明与许可声明 |

---

## 署名与许可 · Authorship & License

- **署名 Signature**：SynomosAI · 诺声(Logos)
- **版权 Copyright**：SynomosAI
- **许可 License**：MIT
- **指纹 Fingerprint**：`FP-MX-3AD01AE9E451`

---

## 权属证明 ATTESTATION · Provenance

`publish_attest.py` 在**本地**为技能包逐文件计算 SHA256，并汇总出包级指纹，写入 `ATTESTATION.md`。整个过程**不发起任何网络请求**——权属证明由你本机算力完成，私钥与令牌无需离开机器，也不依赖任何第三方时间戳或区块链服务（如需锚定外部 TSA / 链上存证，须另行确认后单独执行）。

```bash
python publish_attest.py
```

---

## 安全实测雷达 · Security Radar

`gen_skill_security_radar.py` 读取 `security_results.json`，**确定性**地生成 `security-radar.svg`。图形不含随机量、不含时间戳，相同输入必得相同输出——可复现、可审计，适合作为对外主张的真实依据附件。

```bash
python gen_skill_security_radar.py --results security_results.json
```

---

## 免责声明 · Disclaimer

- 本仓库及技能包**非医疗器械、非医疗软件**，不包含任何疗效或临床声明。
- 采用 **MIT** 许可，**厂商中立**，不绑定任何特定平台或厂商。
- 当前正文为**治理 / 权属框架版**，尚未展开逐步操作教程；具体能力将随版本迭代逐步补全。
- 任何对外主张（性能、效果、合规）**必须挂真实依据**，不得凭空宣称。

---

<p align="center">
  <sub>SynomosAI · 诺声(Logos)</sub>
</p>
