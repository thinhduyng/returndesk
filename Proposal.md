# AI-Assisted Returns Management

**Team:** Thoi Dang Truong Tho (23127487) · Nguyen Duy Thinh (23127122) · Le Anh Duy (23127357)  
**Repository:** [Github](https://github.com/thinhduyng/returndesk)

## 1. Product and Users

A web application for support staff reviewing returns at a small online retailer. Managers maintain policies, approve decisions, and create accounts with support or manager roles; public registration is disabled. Currently, staff manually match informal customer messages and order details to policy documents, making exception handling slow and inconsistent. The application combines request tracking, policy evidence, AI suggestions, and human decisions.

## 2. LLM Feature and Cost of Error

**Policy-grounded request analysis:** extract the problem and requested remedy, retrieve policy passages, recommend handling with citations, and identify missing information. Application code checks order existence and elapsed days; staff approve decisions. Missing or conflicting evidence produces “needs review”.

For example, defective headphones reported after 12 days without packaging require checking defect and packaging policies. If their interaction is unclear, the assistant must flag uncertainty.

On a hypothetical VND 1,000,000 order, a wrong rejection delays the customer's refund; a wrong approval costs the retailer replacement stock and shipping. Suggestions are correctable before action; reopening rejection cannot restore customer time, and recovering shipped goods requires cooperation. The demo uses sample orders without executing refunds or shipments.

## 3. Semester Scope

**In:** one retailer; support and manager roles; login and access control; request creation, filtering, and status tracking; linked sample orders; text policies with version history; cited AI analysis; staff approval, rejection, and follow-up requests; activity history; repeatable evaluation.

**Out:** automatic refunds, payments, shipping labels, live commerce integrations, automated customer messaging, image assessment, fraud detection, multiple retailers or languages, and model training or fine-tuning.

## 4. Six Checkpoints

The team shares implementation. Each owner reviews deliverable quality and completeness before submission; they do not perform all checkpoint work alone. Dates are provisional.

| Checkpoint | Date | Owner | Deliverable |
|---|---|---|---|
| 1. Proposal | 25 Oct 2026 | Nguyen Duy Thinh | Scope, risks, repository, API access check, 10 labelled cases. |
| 2. Design | 8 Nov 2026 | Thoi Dang Truong Tho | Wireframes, data model, policies, retrieval/LLM prototype; measure latency and tokens. |
| 3. Core app | 22 Nov 2026 | Le Anh Duy | Login, requests, orders, policies, manual review workflow. |
| 4. LLM integration | 6 Dec 2026 | Nguyen Duy Thinh | Integrate structured analysis, citations, uncertainty handling, and coded checks. |
| 5. Evaluation | 20 Dec 2026 | Thoi Dang Truong Tho | Evaluate 40+ cases; fix failures; check access control and review usability. |
| 6. Delivery | 3 Jan 2027 | Le Anh Duy | Deployed demo, setup instructions, report, presentation. |

## 5. Two Main Risks

**Unsupported recommendations:** this week, label 10 normal, exception, and incomplete cases; expand to 40+. Check recommendation correctness, citation support, and missing-information detection. Unsupported conclusions fail even if correct. Preserve policy versions and require staff review.

**Integration delay:** this week, test API access with one policy and five requests; validate retrieval, structured output, citations, latency, and cost by checkpoint 2. Build manual processing in parallel and retain it during API failures. Cut interface enhancements first if time runs short.

## 6. Technology Choices

- **React/Vite:** reusable staff dashboard and review components.
- **Node.js/Express:** JavaScript API for requests, policies, and model calls.
- **PostgreSQL:** relational records and audit history; full-text policy retrieval avoids another service.
- **OpenAI GPT-6 Luna (provisional):** structured analysis without model hosting; US$0.10/million input and US$0.50/million output tokens ([pricing](https://developers.openai.com/api/docs/pricing), checked 22 Oct 2026).
- **GitHub/Actions:** shared issues, version control, and automated checks.

At an assumed 3,000 input and 1,000 billable output tokens, analysis costs US$0.0008/call or US$0.80/1,000 calls. Proposed API allowance: US$5, excluding hosting and taxes. Measure actual usage at checkpoint 2 and reassess the model against labelled cases. Keep credentials server-side and send only necessary information.
