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

# Outputs 
1. Order Tracking Agent
<img width="1600" height="718" alt="image" src="https://github.com/user-attachments/assets/8b7d2c01-c181-4aaf-84b8-8667e78129ac" />
2. Product Info Agent 
<img width="1600" height="724" alt="image" src="https://github.com/user-attachments/assets/ada62eee-8d1d-4e48-9fd8-e4f2407cdee3" />
3. Return Order Agent
   <img width="1600" height="453" alt="image" src="https://github.com/user-attachments/assets/783bdaa7-53b2-4379-931c-f4f099a69ed6" />
4. Payement Agent 
<img width="1919" height="859" alt="image" src="https://github.com/user-attachments/assets/92aef8f1-2065-48d9-a4af-37eb02354407" />




