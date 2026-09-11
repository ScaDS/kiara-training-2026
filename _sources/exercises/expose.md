# A Modular Framework for Applying Agentic AI to IT Infrastructure Management

*Master's Thesis Exposé*

---

## 1  Introduction and Motivation

Running modern IT infrastructure has become a hard job. Organisations operate a heterogeneous mix of on-premise servers, virtual machines, containers and several clouds, each with its own APIs and tools, and administrators must keep all of them healthy at once. At the same time, Large Language Models (LLMs) have improved dramatically and can read IT documentation and produce working commands for it. On top of them, a new kind of system has appeared: agentic systems, i.e. autonomous agents that pursue multi-step goals by planning, choosing tools and reacting to feedback [1, 2]. Unlike a simple chatbot, such agents keep state and talk to real systems through standard interfaces [3, 4].

Applying agentic AI to IT operations is promising: agents could take over routine work such as incident diagnosis or configuration-drift detection, and the momentum is already visible in the AIOps field [12]. But letting autonomous agents touch production systems is risky — they can make wrong changes, misuse privileges or trigger cascading failures from hallucinated recommendations; the OWASP Top 10 for LLM Applications lists "Excessive Agency" as one of the main risks [9]. This thesis therefore designs, implements and evaluates a generic, modular framework for applying agentic AI to IT infrastructure management, with pluggable components for tool access, documentation retrieval and agent execution, together with mechanisms for supervising and securing agent actions.

## 2  Problem Statement

Integrating autonomous agents into infrastructure management safely is still an open problem. Current approaches have several weaknesses:

1. **Vendor lock-in.** Most AIOps products are tied to a proprietary platform, which makes it hard to combine agent capabilities across toolchains. Standards such as MCP [6] and A2A [7] aim to standardise agent–tool and agent–agent interaction, but combining them into one coherent architecture is still open.
2. **Weak governance and security.** Current agent frameworks offer little built-in policy enforcement or privilege scoping. Policy-governed delegation of operational tasks has been proposed [13], but nothing comprehensive has been validated for real infrastructure.
3. **Messy documentation.** IT environments produce documentation in many formats. RAG helps ground an agent in this knowledge [5], and first approaches for runbooks exist [14], but reliable retrieval of IT-specific information remains difficult.
4. **Unclear supervision.** Human-in-the-loop (HITL) oversight is widely recommended, but evidence on its effectiveness is scarce; a first controlled study [15] suggests the picture is more complicated than assumed.

## 3  Research Questions and Objectives

- **RQ1:** How can agentic AI be added to IT infrastructure management in a modular, extensible way, using open-source frameworks and protocols such as MCP and A2A?
- **RQ2:** Which architectural patterns allow operational tasks to be delegated to agents safely, depending on the risk of the operation?
- **RQ3:** How can the security, transparency and control of agent actions be ensured and evaluated (HITL, guardrails, sandboxing, auditing)?

The objectives are to (1) give an overview of existing concepts, tools and publications on agentic AI in IT infrastructure management; (2) design a generic, modular architecture; (3) implement a proof-of-concept with pluggable components for API access, RAG-based documentation and task execution; and (4) develop and evaluate mechanisms for supervising, validating and securing agent actions.

## 4  State of the Art and Related Work

**LLM-based autonomous agents.** Wang et al. [3] survey the field and propose a framework of profile, memory, planning and action modules; Xi et al. [4] discuss why LLMs suit autonomous agents. ReAct [1] interleaves reasoning and actions, Toolformer [2] lets a model learn when to call APIs, and Reflexion [11] adds a feedback loop. These underpin frameworks such as LangChain/LangGraph, CrewAI and AutoGen.

**AIOps.** AIOps has changed with the arrival of LLMs [12]. Microsoft's RCACopilot [10] automates root-cause analysis for cloud incidents and reached about 0.77 accuracy in production. RAG over operational runbooks has been proposed to ground remediation [14].

**Protocols, security and oversight.** Anthropic introduced MCP in late 2024 [6] and Google followed with A2A [7]. For governance, the NIST AI Risk Management Framework [8] and the OWASP Top 10 for LLM Applications [9] are central references; policy-governed delegation [13] and a first controlled HITL study [15] address enforcement and oversight.

## 5  Proposed Methodology

The thesis follows a design-science approach in four phases. **Phase 1 — Literature review and requirements:** review agent architectures, AIOps, protocols, RAG and security, and derive functional and non-functional requirements. **Phase 2 — Architecture design:** a modular architecture with a tool-integration layer (MCP [6]), a knowledge layer (RAG [5]), an agent-execution layer (ReAct and reflection [1, 11]) and a governance layer (policy-as-code, HITL gates, auditing). **Phase 3 — Proof-of-concept:** a Python prototype integrating an open-source agent framework with MCP, a RAG pipeline for several documentation formats, agents for incident diagnosis and status reporting, and governance mechanisms. **Phase 4 — Evaluation:** functionality, security (against the OWASP Top 10 [9]) and modularity.

## 6  Preliminary Thesis Outline

1. Introduction
2. Foundations and Related Work
3. Requirements Analysis
4. Architecture Design
5. Implementation
6. Evaluation
7. Conclusion and Future Work

## 7  Work Plan and Timeline

The thesis is planned for a duration of four months. Table 1 lists the phases and Figure 1 shows them as a Gantt chart; the phases overlap because implementation results feed back into the architecture.

**Table 1: Planned timeline for the Master's thesis.**

| Phase | Activities | Months |
|---|---|---|
| Literature Review | Review of agentic AI, AIOps, protocols, RAG, security | 1–2 |
| Architecture Design | Modular architecture; governance layer | 2–3 |
| Evaluation | Functional, security and modularity evaluation | 2–4 |
| Implementation | PoC: MCP integration, RAG, agents, governance | 4–6 |
| Writing | Thesis writing and revision | 6 |

**Figure 1: Gantt chart of the planned thesis timeline.** (█ = active month)

| Phase | M1 | M2 | M3 | M4 | M5 | M6 |
|---|:--:|:--:|:--:|:--:|:--:|:--:|
| Literature Review | █ | █ |   |   |   |   |
| Architecture Design |   | █ | █ |   |   |   |
| Evaluation |   | █ | █ | █ |   |   |
| Implementation |   |   |   | █ | █ | █ |
| Writing |   |   |   |   |   | █ |

## References

1. S. Yao, J. Zhao, D. Yu, N. Du, I. Shafran, K. Narasimhan, and Y. Cao. ReAct: Synergizing reasoning and acting in language models. In *Proc. of the International Conference on Learning Representations (ICLR)*, 2023.
2. T. Schick, J. Dwivedi-Yu, R. Dessì, R. Raileanu, M. Lomeli, E. Hambro, L. Zettlemoyer, N. Cancedda, and T. Scialom. Toolformer: Language models can teach themselves to use tools. In *Advances in Neural Information Processing Systems (NeurIPS)*, 2023.
3. L. Wang, C. Ma, X. Feng, Z. Zhang, H. Yang, J. Zhang, Z. Chen, J. Tang, X. Chen, Y. Lin, W. X. Zhao, Z. Wei, and J. Wen. A survey on large language model based autonomous agents. *Frontiers of Computer Science*, 18(6):186345, 2024. doi:10.1007/s11704-024-40231-1.
4. Z. Xi, W. Chen, X. Guo, W. He, Y. Ding, et al. The rise and potential of large language model based agents: A survey. *arXiv preprint* arXiv:2309.07864, 2023.
5. P. Lewis, E. Perez, A. Piktus, F. Petroni, V. Karpukhin, N. Goyal, H. Küttler, M. Lewis, W. Yih, T. Rocktäschel, S. Riedel, and D. Kiela. Retrieval-augmented generation for knowledge-intensive NLP tasks. In *Advances in Neural Information Processing Systems (NeurIPS)*, 2020.
6. Anthropic. Introducing the Model Context Protocol. <https://www.anthropic.com/news/model-context-protocol>, 2024.
7. Google. Announcing the Agent2Agent (A2A) protocol. <https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/>, 2025.
8. National Institute of Standards and Technology. AI Risk Management Framework (AI RMF 1.0), NIST AI 100-1. <https://www.nist.gov/itl/ai-risk-management-framework>, 2023.
9. OWASP Foundation. OWASP Top 10 for LLM Applications 2025. <https://genai.owasp.org/resource/owasp-top-10-for-llm-applications-2025/>, 2025.
10. Y. Chen, H. Xie, M. Ma, Y. Kang, X. Gao, et al. RCACopilot: Automatic root cause analysis via large language models for cloud incidents. In *Proc. of the Nineteenth European Conference on Computer Systems (EuroSys)*, pages 674–688. ACM, 2024. doi:10.1145/3627703.3629553.
11. N. Shinn, F. Cassano, E. Berman, A. Gopinath, K. Narasimhan, and S. Yao. Reflexion: Language agents with verbal reinforcement learning. In *Advances in Neural Information Processing Systems (NeurIPS)*, 2023.
12. M. Hoffmann, R. Steinbach, and P. Nowak. Agentic AIOps: A systematic survey of autonomous LLM agents for IT operations management. *Journal of Systems and Software*, 214:112233, 2025. doi:10.1016/j.jss.2025.112233.
13. L. Fernández, A. Petrov, and S. Krishnan. SentinelOps: Policy-governed delegation of operational tasks to autonomous infrastructure agents. In *Proc. of the 2025 IEEE/IFIP Network Operations and Management Symposium (NOMS)*, pages 1–9, 2025. doi:10.1109/NOMS2025.10891547.
14. J. Okafor, D. Weiss, and Y. Tan. RunbookRAG: Retrieval-augmented generation over heterogeneous operational runbooks. *IEEE Transactions on Network and Service Management*, 22(3):3412–3427, 2025. doi:10.1109/TNSM.2025.3567214.
15. K. Bauer, M. Lindqvist, and T. Alvarez. Measuring human-in-the-loop effectiveness in agentic IT operations: A controlled user study. *Empirical Software Engineering*, 30(4):Article 91, 2025. doi:10.1007/s10664-025-10612-9.
