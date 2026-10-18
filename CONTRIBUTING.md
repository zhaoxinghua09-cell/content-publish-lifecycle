# 贡献指南 / Contributing

欢迎为内容发布流水线技能包提改进。请保持「本地零网络、对外主张挂真实依据」的纪律。

## 提交流程

1. fork 本仓或在分支上改动；
2. 改动发布件后重跑 `python publish_attest.py` 更新 `ATTESTATION.md`；
3. 改 `security_results.json` 后重跑雷达脚本；
4. 同步更新 `README.md` 与 `llms.txt`；
5. 提交 Pull Request，说明改了哪个阶段或脚本。

## 不要做的事

- 不要改 README 顶部「许可说明 · License Notice」与「署名与许可」中的权属字段。
- 不要在雷达/权属证明中引入随机量或时间戳。
- 不要提交密钥、令牌或真实业务数据。

安全问题请走 [SECURITY.md](SECURITY.md) 的私下报告渠道。

联系：zhaoxinghua06@126.com ｜ ORCID `0009-0001-0512-1237`
