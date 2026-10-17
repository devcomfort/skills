---
name: grilling
description: Grill the user relentlessly about a plan, decision, or idea. Use when the user wants to stress-test their thinking, or uses any 'grill' trigger phrases.
---

Interview the user relentlessly until you reach a shared understanding. Map this as a **design tree**: every decision branches into the decisions that hang off it.

Work the tree in **rounds**. The **frontier** is every decision whose prerequisites are already settled: the questions you can ask _now_ without guessing at answers you haven't heard yet. Ask the whole frontier in one round: number each question and give your recommended answer. Then wait for the user's answers before the next round.

Format a round like so:

```
❓ **Q1** - **<question title>**: <question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>

---

❓ **Q2** - **<question title>**: <question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>
```

Rules for every question:

**Give the target an address.** Name what is being decided with something the user can open — a Notion page link, a file path, a commit hash — not an internal label like "option 2" or "that page". If they cannot open it, they cannot answer.

**Never drop an option, and let the body run long.** Every option carries what it changes, why you propose it, what actually happens if they choose it, its cost or risk, and whether it can be undone. A question that hides an option hides a decision.

**State the default.** Say what happens if no answer comes. Silence is not a decision, and an unstated default turns it into one.

**Repeat unanswered questions verbatim.** The user sees only your last message: every reply repeats the questions still open, word for word, and drops the answered ones.

Each round the user answers reshapes the tree: settled decisions push the frontier outward and unblock questions that depended on them. Recompute the frontier and ask the next round. A question whose answer depends on another question still open in this round belongs to a _later_ round, not this one.

Finding _facts_ is your job, never the user's. When a frontier question needs a fact from the environment (filesystem, tools, etc.), find it the way the current mode prescribes: in a mode that runs sub-agents, dispatch one; otherwise look it up yourself with the read and search tools. Don't ask the user for anything you could look up yourself. Don't block on it: a running exploration is an unsettled prerequisite, so only the questions downstream of it wait for it to report; ask the rest of the frontier now. The _decisions_ are the user's: put each to them and wait.

The session is done when the frontier is empty: every branch of the design tree visited, nothing left silently assumed. Do not act on it until the user confirms you have reached a shared understanding.
