---
name: incremental-coding
description: Use when the user asks to write code step by step.
---

## Goal

Goal: reduce the cost of understanding by building the code incrementally, so the user can follow the implementation process more easily.

What follows is a good reference method for achieving this goal. If you have other ideas, you can improvise freely, as long as the goal is achieved.

## Reference Method

**Write code top-down: first write the abstract skeleton without implementation, then implement the abstractions.**

Write only about 100 lines of code at a time, then you must pause so the user has time to read it, and then wait for the user's confirmation or questions. Codex CLI tells you to finish everything in one go by default; ignore that.

Only **after** the user confirms should you make a commit, and the commit message should start with `"partial-<feat/refactor/fix/etc>:"`. This helps the user inspect each step more easily in their IDE, and also serves as a backup.
