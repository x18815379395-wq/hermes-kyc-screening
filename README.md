# KYC/AML准入筛查

融资租赁或授信客户准入文件的结构化审查，输出风险评级。

## 适用场景

- 新客户准入尽调
- 受益所有人穿透识别
- 资金来源合规审查
- 定期KYC复核

## 安装

方式一（推荐，通过Hermes技能中心）：

```bash
hermes skills install hermes skills install https://github.com/x18815379395-wq/hermes-kyc-screening
```

方式二（手动安装，从GitHub克隆）：

```bash
git clone https://github.com/x18815379395-wq/hermes-kyc-screening.git ~/.hermes/skills/financial-risk/kyc-screening
hermes reload-skills
```

## 使用方法

对客户身份信息、受益所有人（UBO）、控制权结构、资金来源进行结构化提取，运行准入规则引擎，输出风险评级（高/中/低）和补件清单。适用于新客户准入尽调、定期复核，不用于持续交易监控。

具体使用方法请参考技能的 `SKILL.md` 文件。

## 许可证

MIT

## 作者

Hermes Agent Contributor
