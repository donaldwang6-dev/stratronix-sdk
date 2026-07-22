# STRATRONIX Python SDK\n\nBuild custom **private AI agents** that run on the STRATRONIX STA-100 appliance.\n\n## Install\n\n```bash\npip install stratronix-sdk\n```\n\n## Quickstart\n\n```python\nfrom stratronix import Appliance, Agent\n\n# Connect to your on-prem appliance\nappliance = Appliance(host="sta-100.local", api_key="...")\n\n# Define your custom agent\nclass LegalReviewer(Agent):\n    model = "llama-3-70b-instruct-awq-int4"\n    system = "You are a legal contract risk reviewer."\n    \n    def review(self, contract_text: str) -> dict:\n        return self.run(contract_text, response_schema={\n            "risk_clauses": list[str],\n            "severity": list[Literal["low", "medium", "high"]],\n        })\n\n# Run on appliance\nagent = appliance.attach(LegalReviewer())\nresult = agent.review(open("contract.pdf").read())\n```\n\n## Key features\n\n- **Local-only execution**: Zero data ever leaves the appliance\n- **Type-safe schemas**: Pydantic models for structured outputs\n- **Auto-batching**: Multiple agents share the 4090 efficiently\n- **Audit logging**: Every call gets hash-chained to the appliance's audit log\n\n## Documentation\n\n📚 [stratronix-docs](https://github.com/donaldwang6-dev/stratronix-docs)\n\n🛒 [Order an appliance](https://store.stratonix.ai/products/sta-100-paa-standard)\n\n
---

## About STRATRONIX

**STRATRONIX Technology (Shenzhen) Company, Limited** *(鼎图太易信息技术（深圳）有限公司)* is the creator of the Private AI-Agent Appliance (PAA) category.

- 🌐 [www.stratronix.ai](https://www.stratronix.ai)
- 🛒 [store.stratonix.ai](https://store.stratonix.ai)
- 📧 info@stratronix.ai

> Privacy by Design. Open by Source.
