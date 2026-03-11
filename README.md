# Multi Agent Chat Support System using n8n with a Central Manager Agent
Designing a manager-centric multi-agent chat support system in n8n that can reliably handle customer support queries by routing them to specialized agents while maintaining context, control, and correctness.


## Detailed Goal
Building a system where all user messages are first processed by a Manager Agent that acts as the sole decision-maker and orchestrator. The Manager Agent must:
- Understand user intent from free-form messages
- Decide which single specialized agent to invoke per step
- Handle multi-intent queries through sequenced agent execution
- Ask clarifying questions when required information is missing
- Maintain conversation state (order ID, payment ID, pending intent, uploaded docs)
- Enforce strict scope boundaries so agents do not overstep responsibilities
- Handle agent failures, invalid responses, and retries deterministically

Specialized agents are execution-only and limited to:
- **OrderTrackingAgent** → order status & shipment
- **ProductInfoAgent** → product availability & variants
- **ReturnOrderAgent** → returns & refunds
- **PaymentAgent** → payment issues
- **DocAgent** → file upload acknowledgment

Each agent runs as an isolated n8n workflow, invoked only by the Manager Agent.

## Final outcome 
A scalable, debuggable, and deterministic multi-agent chat support system in n8n where:
- The Manager Agent fully controls routing, state, and response flow
- Specialized agents remain simple, focused, and reliable
- Complex customer queries are resolved accurately across multiple turns
- 
## Acceptance Criteria
- All user messages pass through the Manager Agent first
- Correct agent selection in ≥ 95% of cases
- No agent responds outside its defined scope
- Multi-intent queries are handled via ordered agent calls
- Missing data triggers clarification instead of hallucination
- Agent failures are logged and handled gracefully
- Each agent and decision step is traceable within n8n workflows
