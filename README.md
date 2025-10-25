# AI HR System

AI HR System is a secure, extensible conversational HR assistant that combines retrieval-augmented generation (RAG), workflow automation, and integrations to streamline employee lifecycle operations — hiring, onboarding, policy lookup, benefits guidance, and HR analytics.

## Quick overview

- Purpose: Provide fast, consistent, auditable HR answers and automate routine HR tasks so HR teams can focus on strategy.
- Core tech: LLM-backed conversational interface + vector-based retrieval that grounds answers to company documents.
- Deployments: SaaS, cloud-hosted, or on-premise for compliance-sensitive environments.

## Features

- Natural-language Q&A with source citations and versioned policy search.
- Retrieval-augmented generation (RAG) using a vector store to reduce hallucinations.
- Automated workflows: onboarding/offboarding checklists, interview scheduling, task assignment.
- Escalation and human-in-the-loop for sensitive or complex issues.
- Integrations: HRIS, ATS, calendar, ticketing, SSO (SAML/OAuth).
- Analytics and reporting: trending questions, coverage gaps, usage metrics.
- Security & governance: role-based access, PII redaction, audit logging, configurable retention.

## Repository layout

- `ai_hr_assistant.py` — main assistant script / entry point (project-specific code).
- `requirements.txt` — Python dependencies.
- `Backup/` — older project snapshots and sample docs.
- `AI_HR_Setup_Guide.md`, `setup_guide.md` — setup notes and deployment tips.

## Installation (local, development)

Prerequisites: Python 3.10+ and a virtual environment.

PowerShell example:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
```

## Running the assistant (dev)

Run the main script (adjust args/config as needed):

```powershell
python .\ai_hr_assistant.py
```

If the project expects environment variables (API keys, DB URLs, etc.), set them in your environment or a `.env` file before launching.

## Configuration

- Document ingestion: point the ingestion pipeline at your policy and handbook documents. The system builds a vector index and attaches metadata (source, version, tags).
- Connectors: configure adapters for HRIS/ATS, calendar and ticketing in a `connectors/` config or environment-backed secret store.
- Access control: configure role mappings and RBAC policies so sensitive documents are only accessible to authorized roles.

## Security & privacy notes

- Use least-privilege API keys for integrations and rotate them regularly.
- Encrypt documents and vector store at rest, and enforce TLS in transit.
- Implement PII redaction and consent checks before including employee data in prompts or indexes.
- Enable audit logging for interactions and escalations to maintain compliance records.

## Common use-cases

- Employees: ask about leave policy, benefits, or how-to procedures.
- HR: auto-respond to FAQs, run onboarding/offboarding checklists, and reduce repetitive ticket load.
- Recruiters: automate interview scheduling and answer candidate questions at scale.

## Examples (sample prompts)

- "How many paid sick days do I have under the current policy?"
- "What steps should I follow to onboard a new contractor in the UK?"
- "Create an onboarding checklist for a product manager role and assign tasks to People Ops."

## Operational guidance

- Monitor model usage and token costs; use RAG to limit expensive LLM calls.
- Add human review for high-risk answers and maintain an approvals workflow for policy changes.

## Contributing

1. Fork the repository and create a topic branch.
2. Add or update tests where applicable.
3. Open a PR with a description of changes.

## License

Include your project license here (e.g., MIT, Apache-2.0) or replace this section with your organization's licensing terms.

## Contact & support

For setup and integration help, see `AI_HR_Setup_Guide.md` or open an issue in this repository.

---

Created: README for `AI HR System` — explains purpose, installation, security and operational guidance.
