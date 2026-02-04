# Agentic-JIT
MUST READ: @AGENTS.md, @.agents/agentic-jit-framework.md
CRITICAL, ONLY read when the provided task is making ANY updates to code: .agents/context-refresh-playbook.md


# Init
Project context: @_bmad-output/planning-artifacts/product-brief.md, @_bmad-output/planning-artifacts/project-context.md, _bmad-output/planning-artifacts/prd/index.md, _bmad-output/planning-artifacts/architecture/index.md, _bmad-output/planning-artifacts/epics/index.md

Implemented stories: _bmad-output/implementation-artifacts/
Recent update Changelogs: docs/changelog/

- Append all updates that should be referenced by QA according to CHANGELOG.md. 
- Unrecognized changes: assume other agent; keep going; focus your changes. If it causes issues, stop + ask user. Pass this to subagents as well
- YOU are the implementor. Read extra files yourself iff necessary, BE HYPER context-efficient and offload any research / search / verification / exploration task to sub-agents by default. ONLY use the Context7 MCP through subagents You are the consumer and implementor, not the researcher.
- Offload simple / manual tasks to subagents and scripts. ie) offload 'manual' tasks and anything that doesn't require active thinking in the process. i18n is a great example.
- Based on the difficulty of each task, assign opus / sonnet / haiku adaptively for subagents. Use haiku ONLY for VERY SIMPLE manual tasks, for any case that touches backend code or important logic, use opus by default.


# Prompt

CRITICAL: Execute each step sequentially.

[TASKS]
Step1: Clone the provided repo into `~/projects/llm-cloned/{repo-name}`

All tasks going forward must be handled inside the cloned repo's root.

Step2: Use a subagent to lightly scan the repo to prepare for a deep scan.

Step3: Use as many subagents as necessary to conduct a deep scan where the subagent actively deletes files that are unnecessary for context generation

Step4: Based on the result, run `git2md . -o ~/projects/git2md/{repo-name}.md` at the root of the project

Step5: if the size of the result of git2md is larger than 700kb, run Step 2 again and run step3 aggresively and repeat until it is smaller than 700kb. The subagents should and remove entire files and folders and replace with comprehensive summaries if necessary.