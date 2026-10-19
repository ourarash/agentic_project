# EE 599: Agentic Application Project

**Draft · Fall 2026 · Individual project; no teams**

Build a complete agentic application for a specific user and task. Your application should choose actions based on intermediate results, use tools, and produce an outcome the user can inspect. Evaluate how well it works, use the evidence to make one improvement, and evaluate it again.

Choose a narrow problem you can finish within the course workload. A CLI, notebook, or simple web interface is sufficient. You may extend your own assignment code. Multiple agents, RAG, browser automation, and multimodal inputs are optional.

## Getting started

This repository contains the project brief. Create your own project repository using Python 3.11 or newer and Git. Choose dependencies for your application and document installation, configuration, and commands for running the application, tests, and evaluation. Keep credentials out of Git; provide an `.env.example` with placeholder values if needed.

## Choose a subject

Choose an option below or propose your own. Identify the user, task, and reason for using an agent.

| Subject | Example scope | Example success criteria |
|---|---|---|
| Research assistant | Investigate a narrow question, search sources, and produce a cited brief. | Supported claims, accurate citations, and recognition of missing evidence. |
| Coding assistant | Investigate an issue in a small repository, propose a patch, and run tests. | Relevant tests pass; changes address the issue without breaking existing behavior. |
| Data analysis assistant | Inspect a public dataset, choose analysis steps, run code, and explain results. | Correct calculations, reproducible analysis, and handling of missing data. |
| Course or lab assistant | Consult documentation, diagnose a setup problem, and guide troubleshooting. | Correct diagnosis, useful steps, and escalation when evidence is insufficient. |
| Service request assistant | Consult policies, ask for missing information, and update a mock ticket after approval. | Correct decisions, valid updates, and no action without approval. |
| Trip or event planner | Gather constraints, compare options, and revise an itinerary. | Feasible schedules, correct costs, and satisfaction of user constraints. |

Use public or synthetic data. Mock services and local sandboxes are acceptable.

## Application requirements

Your **first version** must:

- Complete one useful workflow from user input to an inspectable result.
- Use at least two meaningful tools, including one capability connected through MCP.
- Track explicit execution state, validate tool arguments, handle tool errors, and enforce a step or cost limit with a stop condition.
- Record model/tool calls, outcomes, cost, and elapsed time.
- Require human approval before a tool sends a message, spends money, or changes/deletes user or external data. Test this in a sandbox or mock service when appropriate.

Your **final version** must also save execution state and recover after interruption without repeating completed external actions. Implement one memory rule: explain what persists across runs and how it can be corrected or forgotten. Use a failed trace to motivate one change, test it, and keep or undo it based on results. Document permissions, prompt-injection risks, defenses, and limitations.

Use the course tools or check with the instructor before choosing alternatives.

## Required evaluation

**A demonstration alone is insufficient.** Evaluate the complete application, including its actions and final results.

1. **Define test cases and success criteria.** Submit at least 10 cases for the first version and 20 for the final version. Each case needs an input, starting data/state, and an expected outcome or scoring rubric. Include ordinary tasks, ambiguous or missing information, and tool failures. Final cases must also test denied approval, interruption/recovery, and prompt injection.
2. **Compare against a simple baseline.** Use a single model call or fixed workflow. Explain its access to information/tools and record model settings and execution budgets for a fair comparison.
3. **Measure outcomes and effort.** Report task success rate, relevant quality scores, control/recovery test results, cost per task, and elapsed time. Use automated checks where possible. If using an LLM judge, submit its rubric/prompt and manually check at least five judgments, reporting disagreements.
4. **Test improvement fairly.** Reserve at least five final cases from development. Freeze the final set and run the baseline, first version, and final version on it. Do not tune on reserved cases. Repeat five final-agent cases three times each to examine variability; report these separately.
5. **Explain failures.** Analyze at least two failed cases using execution traces. Show before-and-after results for your chosen change, including regressions or an unsuccessful improvement.

Submit cases, evaluation code, saved results, and a command to reproduce the evaluation. Reset state between cases unless testing memory across runs. Include failures and timeouts. Version source data where possible, document live dependencies, and estimate costs before large runs.

Tool and control-logic tests may use mocks and run offline. End-to-end evaluation must also run the application with an actual model, hosted or local. Identify the model used and distinguish mocked test results from measured application results. For local models, report token usage and elapsed time even if there is no API charge.

## Deadline timeline

**Proposed schedule:** dates and submission times will be confirmed in the LMS. Week 6 subject selection replaces the syllabus's Week 5 project-plan milestone in this draft.

| Deadline | Deliverable |
|---|---|
| **End of Week 6** | **Subject selection only:** a title and 2–3 sentences identifying the user and task. No code, design, or evaluation plan required. |
| **End of Week 7** | A plan of at most one page: scope, tools, baseline, and measurements. Attach 10 evaluation cases with success criteria. |
| **End of Week 8** | **First version:** runnable application, system diagram, setup/evaluation instructions, baseline comparison, two failure analyses, and improvement plan. Preserve this version with a Git tag. |
| **End of Week 11** | Progress check: demonstrate saved state, interruption/recovery, the memory rule, and approval behavior. |
| **End of Week 14** | Draft final results and revised threat model, including findings from the class security exercise. |
| **Week 15 class** | Present the application, system design, measured results, costs, failures, and limitations. Include a short live or recorded demonstration. |
| **Final-period deadline** | **Final version:** reproducible repository, evaluation cases/code/results, representative traces, final report of at most four pages excluding references, and presentation materials. |

Planning and progress checkpoints receive feedback and are not separately graded. Submit graded work through the LMS.

## Grading and submission

The first and final versions each count for **30% of the course grade**. Within each submission: application functionality and design **30%**; evaluation and interpretation **30%**; reliability, human control, and security **20%**; reproducibility and explanation **20%**. Assessments reflect the requirements taught by that stage. The final-version grade includes the presentation.

Evaluation is graded on credible methods, reproducible evidence, and honest interpretation. Perfect success rates or positive improvement results are not required for full credit.

A fresh checkout must run using documented setup, sample data, and test/evaluation commands. Document required environment variables; never submit keys. Follow the syllabus AI-use and data policies and be able to explain and modify your code.

Include the syllabus verification note: models used by the application/evaluation; how you tested it; and one known failure or limitation. The final report should also briefly identify your own implementation and any reused code or components.

For each graded submission, push your work and submit the repository URL and exact commit hash through the LMS, together with the required report/results. Ensure the instructor can access the repository and include or link all required artifacts. Use the LMS for subject selection and feedback checkpoints as well. A GitHub push alone is not a submission.

## References and useful resources

Optional starting points; select those relevant to your subject. Production case studies exceed the expected project scope.

- [Building Effective Agents — Anthropic](https://www.anthropic.com/engineering/building-effective-agents): start here for workflow choices, tool design, and support/coding application examples.
- [ReAct — Yao et al.](https://arxiv.org/abs/2210.03629): a paper on interleaving model decisions with actions and external observations.
- [How We Built Our Multi-Agent Research System — Anthropic](https://www.anthropic.com/engineering/multi-agent-research-system): search, citations, evaluation, and cost tradeoffs in a research-assistant case study.
- [Raising the Bar on SWE-bench Verified — Anthropic](https://www.anthropic.com/engineering/swe-bench-sonnet): a coding-agent case study showing how tools and the execution loop affect results.
- [OpenAI Agents SDK](https://openai.github.io/openai-agents-python/): implementation documentation for agents, tools, handoffs, and tracing.
- [LangGraph Overview](https://docs.langchain.com/oss/python/langgraph/overview): an entry point for stateful execution, persistence, and human intervention.
- [MCP Architecture](https://modelcontextprotocol.io/docs/learn/architecture): how hosts, clients, servers, tools, and resources fit together.
- [Evaluate Agent Workflows — OpenAI](https://developers.openai.com/api/docs/guides/agent-evals): guidance and tooling for reproducible agent evaluation.
- [Reflexion — Shinn et al.](https://arxiv.org/abs/2303.11366): using feedback and saved reflections to improve later attempts without training model weights.
