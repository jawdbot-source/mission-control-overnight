# Mission Control (Usable Workboard)

Mission Control is now a **functional execution board**, not a static mock.

## What works now

- Editable task board with 4 lanes: **Now / Next / Blocked / Done**
- Click any task card to open full detail editor
- Update status, priority, owner, link, and definition-of-done
- Add/delete tasks
- Copy a generated **execution brief** from live board state (timestamped with owners + fast links)
- Add timeline/feed updates
- Export/import board JSON
- Persist board changes in browser `localStorage`
- Reset back to baseline `state.json`
- **10-second workflow map** at top to orient Plan → Edit → Unblock → Share instantly
- Live orientation line summarizes current mode (executing/blocked/ready/setup) in one sentence
- Numbered quick-navigation chips (1→4) jump directly to Workboard, Task details, Strike desk, and Recent updates
- Start-here focus strip calls out the top action, explains **why** it is first, shows a live **Then** follow-up step, and includes a single dynamic **Step 1** recommended-action button plus contextual Focus Now/Blocked/Next controls
- Mission-path strip shows the live top Now/Blocked/Next tasks in one glance
- Immediate-command strip gives a live 3-step directive (open/move/copy) for the current board state
- Current-context trail shows exactly where you are (lane + selected task) at all times
- Board-freshness strip shows the latest logged update and timestamp at a glance
- Lane guide explains Now/Next/Blocked/Done semantics at a glance directly above the board
- Lane highlight flash gives immediate visual confirmation when tasks are saved/moved
- Lane color system (Now/Next/Blocked/Done) improves scan speed and visual polish
- Phase pill (blocked/executing/ready/setup) and lane-colored counters make board state legible at a glance
- Board-health strip summarizes execution state instantly (blocked/executing/ready/empty)
- TL;DR strip gives a one-line immediate directive from live board state
- Keyboard shortcut strip speeds first actions: `N` add task, `F` open first action, `C` copy brief
- Accessibility baseline: skip link, visible keyboard focus states, aria-live action feedback, reduced-motion support, and dialog semantics for task modal
- Action status line confirms control results (save/open/copy/import/export/reset)
- Open-link control is context-aware and disabled until a valid task link is present
- Execution flow controls: pull/unblock/complete buttons show live top task labels, disable when empty, and auto-pull top Next after completing final Now task
- Strike Desk section for Strike coordination (policy guardrail, focus list, notes, copyable strike brief)

## Files

- `index.html` — UI + behavior
- `state.json` — baseline board content

## Run locally

```bash
cd /Users/openclaw/projects/strike-dd/ops/mission-control
python3 -m http.server 8091
# open http://127.0.0.1:8091/
```

## Quality gate (manual smoke test)

Before calling it "ready", verify:

1. Click a task card → details panel opens with task values.
2. Edit title/status/priority and click **Save task**.
3. Refresh the page → edited values persist.
4. Click **Copy execution brief** and confirm clipboard content changed.
5. Add a feed item and a new task.
6. Export JSON, reset to baseline, then import JSON and verify restore.

If any check fails, it is **not done**.
