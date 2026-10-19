# EE 599: Agentic Application Project

**Draft · Fall 2026 · Individual project; no teams**

Build an AI-agent application for a specific user and task. The agent must use tools, choose actions based on what it finds, and produce a result the user can check. Measure how well it works, make one change based on the results, and measure it again.

Choose a small problem you can finish within the course workload. A command-line interface, notebook, or simple web interface is sufficient. You may extend your own assignment code. Add multiple agents, document retrieval, browser automation, or image/audio inputs only when they help with your task.

## Getting started

Create your own repository using Python 3.11 or newer and Git. Document package installation, configuration, and commands to run the application, tests, and evaluation. Keep passwords and API keys out of Git. Provide an `.env.example` with placeholder values for any required environment variables.

## Choose a subject

Choose an option below or propose your own. Explain who will use it, what task it will complete, and why the agent needs to choose actions as it works.

| Subject | What the application could do | How you could check success |
|---|---|---|
| Research assistant | Investigate a narrow question, search sources, and write a brief with citations. | Sources support the claims; citations are accurate; missing evidence is identified. |
| Coding assistant | Investigate an issue in a small repository, propose a patch, and run tests. | Relevant tests pass; changes address the issue without breaking existing behavior. |
| Data analysis assistant | Inspect a public dataset, choose analysis steps, run code, and explain results. | Calculations are correct; another person can repeat the analysis; missing data is handled. |
| Course or lab assistant | Read documentation, diagnose a setup problem, and guide troubleshooting. | Diagnosis and steps are useful; the agent asks for help when it lacks evidence. |
| Service request assistant | Read policies, ask for missing information, and update a simulated ticket after approval. | Decisions and updates follow policy; approval is required before an update. |
| Trip or event planner | Gather user requirements, compare options, and revise an itinerary. | Schedules are feasible, costs are correct, and the plan meets user requirements. |

Use public or made-up data. You may simulate external services and run actions in a local test environment.

## Application requirements

Your **first version** must:

- Complete one useful task from user input to a result the user can check.
- Use at least two useful tools, with at least one capability connected through Model Context Protocol (MCP), the standard introduced in class.
- Track progress in explicit state, such as completed steps and tool results. Check tool arguments, handle tool errors, and stop when a step or cost limit is reached.
- Save an execution trace: a record of model calls, tool calls, and their results. Record cost and elapsed time as well.
- Require human approval before a tool sends a message, spends money, or changes or deletes user or external data. You may demonstrate this with simulated services.

Your **final version** must also:

- Save progress and resume after an interruption without repeating completed external actions.
- Implement one memory rule: explain what information is kept across runs and how it can be corrected or deleted.
- Use a trace from a failed run to choose one change. Test the change and keep or undo it based on the results.
- Explain what the application can access or change, how it handles prompt injection (instructions hidden in outside content), and what risks remain.

Use the course tools or check with the instructor before choosing alternatives.

## Required evaluation

**Evaluation is required.** Test whether the complete application takes appropriate actions and produces correct results.

1. **Define tasks and success criteria.** Submit at least 10 cases for the first version and 20 for the final version. Each needs an input, starting data and state, and an expected outcome or scoring guide. Include ordinary tasks, unclear requests, missing information, and tool failures. Final cases must also test denied approval, interruption and recovery, and malicious instructions in outside content.
2. **Compare with a simpler approach.** Your baseline could be a single model call or fixed sequence of steps. Explain its access to information and tools. Record model settings and step or spending limits so readers can assess the comparison.
3. **Measure results and effort.** Report the percentage of successful tasks, relevant quality scores, approval and recovery results, cost per task, and elapsed time. Automate checks where possible. If a model scores outputs, submit its instructions and scoring guide, manually check at least five judgments, and report disagreements.
4. **Check improvement on unfamiliar tasks.** Reserve at least five final cases that you do not use to adjust the application. Finalize the test set before comparing the baseline, first version, and final version; run all three on the same cases. Run five final-version cases three times each and report how results vary.
5. **Explain failures.** Use traces to analyze at least two failed cases. Show results before and after your chosen change, including any tasks that became worse or stayed the same.

Submit cases, evaluation code, saved results, and a command to repeat the evaluation. Reset state between cases unless testing memory across runs. Count failures and timeouts. Save or version source data where possible, identify required live services, and estimate costs before large runs.

Tool and control-logic tests may use fixed responses offline. Evaluation of the complete application must also use an actual model, hosted or local. Identify the model and label simulated results. Report tokens processed and elapsed time for local models, even without an API charge.

## Deadline timeline

**Proposed schedule:** dates and times will be confirmed in the course learning-management system (LMS). Week 6 subject selection replaces the syllabus's Week 5 project-plan deadline in this draft.

| Deadline | Deliverable |
|---|---|
| **End of Week 6** | **Subject selection only:** a title and 2–3 sentences identifying the user and task. No code, design, or evaluation plan required. |
| **End of Week 7** | A plan of at most one page: task and scope, tools, simpler approach for comparison, and measurements. Attach 10 test cases with success criteria. |
| **End of Week 8** | **First version:** working application, system diagram, setup and evaluation instructions, baseline comparison, analysis of two failures, and improvement plan. Save a Git tag marking this version. |
| **End of Week 11** | Progress check: demonstrate saved progress, recovery after interruption, memory across runs, and approval behavior. |
| **End of Week 14** | Draft final results and revised threat model: the possible attacks, defenses, and remaining risks. Include findings from the class security exercise. |
| **Week 15 class** | Present the application, system design, measured results, costs, failures, and limitations. Include a short live or recorded demonstration. |
| **Final-period deadline** | **Final version:** repository another person can run, evaluation cases and code, saved results, example traces, presentation materials, and a report of at most four pages excluding references. |

Planning and progress checkpoints receive feedback and are not separately graded. Submit graded work through the LMS.

## Grading and submission

The first and final versions each count for **30% of the course grade**. Each submission is graded on:

- **30%:** whether the application works and its design fits the task.
- **30%:** evaluation quality and explanation of results.
- **20%:** reliability, human control, and security.
- **20%:** whether another person can run the work and understand your explanation.

Grading reflects the requirements taught by that stage. The final-version grade includes the presentation.

Evaluation is graded on sound methods, results others can reproduce, and honest interpretation. You can earn full credit even if tasks fail or your change does not improve results.

Another person must be able to run a fresh copy of your repository using your instructions and sample data. Follow the syllabus AI-use and data policies. Be able to explain and modify your code.

Include the syllabus verification note in three bullets: models used; how you tested the work; and one known failure or limitation (or “none found”). In the final report, identify what you built and any reused code or components.

Push each graded submission and submit its repository URL, exact commit hash, report, and results through the LMS. Check that the instructor can access everything. Submit subject selection and feedback checkpoints through the LMS as well.

## References and useful resources

These resources are optional. Choose those that help with your subject. The industry case studies describe larger systems than this project requires.

- [Building Effective Agents — Anthropic](https://www.anthropic.com/engineering/building-effective-agents): start here for workflow choices, tool design, and support/coding application examples.
- [ReAct — Yao et al.](https://arxiv.org/abs/2210.03629): how a model alternates between choosing actions and using the information those actions return.
- [How We Built Our Multi-Agent Research System — Anthropic](https://www.anthropic.com/engineering/multi-agent-research-system): search, citations, evaluation, and cost tradeoffs in a research-assistant case study.
- [Raising the Bar on SWE-bench Verified — Anthropic](https://www.anthropic.com/engineering/swe-bench-sonnet): a coding-agent case study showing how tools and the execution loop affect results.
- [OpenAI Agents SDK](https://openai.github.io/openai-agents-python/): documentation for agents, tools, passing tasks between agents, and recording runs.
- [LangGraph Overview](https://docs.langchain.com/oss/python/langgraph/overview): managing state, saving progress, and pausing for human input.
- [MCP Architecture](https://modelcontextprotocol.io/docs/learn/architecture): how hosts, clients, servers, tools, and resources fit together.
- [Evaluate Agent Workflows — OpenAI](https://developers.openai.com/api/docs/guides/agent-evals): guidance and tools for evaluations that can be repeated.
- [Reflexion — Shinn et al.](https://arxiv.org/abs/2303.11366): using feedback and saved reflections to improve later attempts without training model weights.
