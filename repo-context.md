<Init>
- Append all updates that should be referenced by QA according to CHANGELOG.md. 
- Read extra files iff necessary, BE HYPER context-efficient and offload any research / search / verification / exploration task to sub-agents by default. You are the consumer and implementor, not the researcher.
- Offload simple / manual tasks to subagents and scripts. ie) offload 'manual' tasks and anything that doesn't require active thinking in the process. i18n is a great example.
- Based on the difficulty of each task, assign opus / sonnet / haiku adaptively for subagents. Use haiku ONLY for VERY SIMPLE manual tasks, for any case that touches backend code or important logic, use opus by default.
</Init>

CRITICAL: Execute each step sequentially.

[TASKS]
Step1: Clone the provided repo into `~/projects/llm-cloned/{repo-name}`

All tasks going forward must be handled inside the cloned repo's root.

Step2: Use a subagent to lightly scan the repo to prepare for a deep scan.

Step3: Use as many subagents as necessary to conduct a deep scan where the subagent actively deletes files that are unnecessary for context generation

Step4: Based on the result, run `git2md . -o ~/projects/git2md/{repo-name}.md` at the root of the project

Step5: if the size of the result of git2md is larger than 700kb, run Step 2 again and run step3 aggresively and repeat until it is smaller than 700kb. The subagents should and remove entire files and folders and replace with comprehensive summaries if necessary.