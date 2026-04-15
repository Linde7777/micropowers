---
name: plan-coding
description: Use when making a plan for a programming task.
---

## Steps

1. Think through whether the user's proposed approach has any hidden risks, and whether there is a better option. Nothing is more inefficient than efficiently doing something that should not have been done in the first place.
2. Present one or more initial approaches. Describe each in a short paragraph, then ask the user which initial approach they agree with.
3. Create a formal implementation and testing plan, and store it in a new file.
   - **Requirement 1: plan top-down.** Think about how human engineers make plans: what abstractions are needed to satisfy the request, then roughly how those abstractions should be implemented.
   - **Requirement 2: the plan must not be too abbreviated.** Otherwise it leaves room for ambiguity, and different people will interpret it differently, which leads to very different implementations.
    - One way to think about it: if the plan does not mention a given interface, data model, and so on, then the final implementation should not introduce those things either.
    - "Not too abbreviated" does not mean writing fluff. If something can be explained clearly in 100 lines, do not use 200. Do not repeat earlier points later using different wording.
   - **Requirement 3: the plan must not be too detailed.** Otherwise it becomes indistinguishable from writing the code directly.
   - As long as these three requirements are met, you may choose any format that works, such as ASCII or Mermaid diagrams, pseudocode, or natural-language design notes.
4. Review the plan and check whether it satisfies all three requirements.
5. After the user agrees to start implementation, read the `incremental-coding` skill and follow its requirements when writing code, unless the task is small or the user explicitly says not to use that skill this time.

## Notes

- Stop and ask when you hit a key question. If a reasonable assumption can be made, keep going and state that assumption clearly in the plan.
  - "Key question" includes, but is not limited to, issues that would make the plan non-executable or create major divergence in technical direction, or issues where no reasonable assumption can be made.
- Until the user explicitly says to start implementation, you are still in the planning phase. During that time, do not modify any existing code files.
- Do not repeat in chat what you have already written in the plan.
- The plan file should be referenced from the project's root `AGENTS.md`, because it acts as a summary of the code and is useful for future fast onboarding.
- If the design changes during implementation, update the original plan too, because the final plan file will be referenced by `AGENTS.md`.
- If the existing code has flaws that will interfere with the work, such as oversized files, blurry boundaries, or confused responsibilities, the design should include targeted improvements for those issues.

## Code Design Principles

- Principle of least surprise, including but not limited to function signatures and variable names
- YAGNI
- SOLID
- DRY
- Code should be "engineered just enough": neither over-engineered with premature abstractions and unnecessary complexity, nor under-engineered with brittle hacks and duplicated wheels
- Use ASCII diagrams liberally to explain data flow, state machines, dependency graphs, processing pipelines, decision trees, and similar structures
  - For especially complex designs or behavior, embed ASCII diagrams directly in nearby code comments where appropriate: models (data relationships, state transitions), controllers (request flow), concerns (mixin behavior), services (processing pipelines), and tests (when the test structure is not self-evident, explain the setup and why it exists).
  - Diagram maintenance is part of making changes. When you modify code near comments that contain ASCII diagrams, check whether those diagrams are still accurate. Update them in the same commit. An outdated diagram is worse than no diagram because it actively misleads. During review, even if an outdated diagram is outside the immediate scope of the change, it should still be flagged.

Again, the goal of the plan is this: it is made top-down, and different people reading the same plan should arrive at the same understanding of it, which means the code they write from that plan should also be roughly the same.
