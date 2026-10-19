# Enterprise AI Knowledge & Action Hub

A portfolio demonstration of an enterprise AI agent that combines grounded knowledge retrieval, PostgreSQL data, authorization, and evidence-aware answers.

## Live links

- [Start here: portfolio home](https://mattxhl.github.io/enterprise-ai-portfolio/)
- [Architecture & engineering decisions](https://mattxhl.github.io/enterprise-ai-portfolio/03-architecture.html)
- [Open the live Cloud Run demo](https://enterprise-ai-frontend-655698171583.us-west1.run.app)
- [View the public reader demonstration](https://mattxhl.github.io/enterprise-ai-portfolio/01-public-reader-demo.html)
- [View the role access demonstration](https://mattxhl.github.io/enterprise-ai-portfolio/02-role-access-demo.html)
- [Browse this portfolio repository](https://github.com/mattxhl/enterprise-ai-portfolio)

## Access the live demo

Start with the screenshot walkthroughs; they require no account. To use the live application, request assigned demo credentials from Matthew Xu. The reader account covers policy questions; HR reader permits employee queries; HR writer permits proposals and explicit approval/rejection. Writer self-approval is an intentional demo policy. The demonstrated writer path ends in rejection without a salary change.

## What the demo demonstrates

The public reader experience shows:

1. **Grounded answer with evidence** — the Calgary parking question returns the approved amount and cites its source.
2. **Authorization boundary** — the highest-paid employee question is denied because the public reader lacks the `employee_data_reader` role.
3. **Insufficient-evidence abstention** — the unsupported pet-llama policy question is declined when evidence is below the answer threshold.

See the [full screenshot walkthrough](https://mattxhl.github.io/enterprise-ai-portfolio/01-public-reader-demo.html).

## Role access walkthrough

The [local role demonstration](https://mattxhl.github.io/enterprise-ai-portfolio/02-role-access-demo.html) compares reader, HR reader, and HR writer accounts. It shows:

- The same employee query denied for the reader and answered for the HR reader.
- A pending salary-change proposal followed by rejection, without executing the change.
- A multi-step salary comparison with expandable execution-inspector evidence.
- Upload denials for all three normal accounts.
- Successful ingestion with a temporary `knowledge_manager` grant, duplicate detection, and cited retrieval. The temporary grant was removed after testing.

These screenshots were captured locally. Hosted sign-in is now enabled for assigned demo accounts; reader access, HR-reader queries, and writer proposal/rejection were also verified in the hosted app. Successful knowledge upload used a temporary local management-role grant.

## Technical highlights

- Streamlit frontend backed by FastAPI
- PostgreSQL and pgvector
- Retrieval-augmented generation with source citations
- Role-based authorization before protected tool access
- Evidence thresholds and safe abstention
- Google Cloud Run deployment
- Neon PostgreSQL with SSL
- Secret Manager and automated Cloud Build release validation

## Deployment evidence

The release pipeline:

1. Builds and tests the backend and frontend images.
2. Runs database migrations.
3. Deploys both Cloud Run services.
4. Verifies that the new revisions are Ready with 100% traffic.

Hosted demo login is enabled. Request demo credentials from Matthew Xu; passwords are not published in this repository. The private development repository contains the implementation, tests, and deployment configuration.

## Screenshot

![Public reader demo](docs/screenshots/01-public-reader-demo.png)
