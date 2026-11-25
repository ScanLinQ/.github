# ScanLinQ

ScanLinQ is an AI gateway and workflow builder that lets you call workflows like models. Design logic visually, test workflows, and invoke them by name from your existing SDK. If a provider fails, ScanLinQ automatically reroutes to your next preferred option.

### Workflows

- Build workflows visually by starting from a template or a blank canvas. Each step can review or refuse a request, respond directly, call one or more models, consult a judge, review attached documents, or notify your team.
- Test workflows before deployment by writing test cases and running them on any saved version.
- Each save creates a new version. You can activate a previous version to roll back changes.
- Review each run to see the steps taken, outcomes, model calls, and associated costs.
- Access a workflow gallery to import and adapt workflows published by other ScanLinQ users.

### The gateway

- Enable automatic failover by chaining models, so requests are rerouted if a provider fails or rejects them. You don't need to write retry logic.
- Use your own provider keys, which are envelope-encrypted with AWS KMS for security.
- View detailed metrics for each request, including latency, token usage, and cost.
- Access built-in usage dashboards, a multi-modal playground for up to six models side by side, and a model directory organised by vendor API and region.

### Get started

1. Create an account at [scanlinq.com](https://scanlinq.com) and connect your provider keys.
2. Issue a gateway key and set your SDK's `base_url` to ScanLinQ.
3. Build a workflow and invoke it by name:

```python
from openai import OpenAI

client = OpenAI(base_url="<your ScanLinQ gateway URL>/v1", api_key="slq_...")

reply = client.chat.completions.create(
    model="@workflow/support-triage",  # your workflow, by name
    messages=[{"role": "user", "content": "My order hasn't arrived."}],
)
```

ScanLinQ is currently in early access and free, with billing disabled.

[Website](https://scanlinq.com) · [LinkedIn](https://www.linkedin.com/company/139823906) · Built by [Encype](https://encype.com)
