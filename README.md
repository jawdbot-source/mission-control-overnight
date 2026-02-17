# Mission Control (Usable Workboard)

Mission Control is now a **functional execution board**, not a static mock.

## What works now

- Editable task board with 4 lanes: **Now / Next / Blocked / Done**
- Click any task card to open full detail editor (auto-jumps to Task details panel)
- Task details header shows live context (lane, priority, owner) for the selected task
- On load/import/reset/delete, task selection defaults to top-priority Now → Blocked → Next → Done item
- Update status, priority, owner, link, and definition-of-done
- Add/delete tasks
- Copy a generated **execution brief** from live board state (timestamped with board mode/lane counts, owners, and fast links)
- Add timeline/feed updates
- Export/import board JSON
- Persist board changes in browser `localStorage`
- Reset back to baseline `state.json`
- **10-second workflow map** at top to orient Plan → Edit → Unblock → Share instantly
- Sticky top command surface keeps orientation/actions visible while scrolling through details
- Live orientation lines summarize current objective + mode + a 10-second quick-summary line + a dynamic workflow compass + a three-click path + "Step X of 4" position, include section-specific goal + action lines, show an at-a-glance board snapshot + workflow progress percentage, and provide a one-click **Next step** button
- Numbered quick-navigation chips (1→4) jump directly to Workboard, Task details, Strike desk, and Recent updates, with active-section highlighting, jump confirmation feedback, and live status labels (executing/blocked/ready, selected task, update freshness)
- Section headings mirror the same 1→4 numbering for instant map-to-panel alignment
- Every major section now includes a one-line “Purpose” statement to make panel intent obvious on first scan
- Panel sections now use intentional visual accents by function (task/brief/validation/heartbeat/strike/updates) for faster scanning and cleaner polish
- Heading typography now has clear hierarchy (stronger section titles, lighter panel labels) for a more finished visual system
- Primary action bar is numbered (1→5) to reinforce a predictable execution order
- Start-here focus strip calls out the top action, explains **why** it is first, shows a live **Then** follow-up step, and includes a single dynamic **Step 1** recommended-action button plus contextual Focus Now/Blocked/Next controls
- Mission-path strip shows the live top Now/Blocked/Next tasks in one glance and each chip jumps directly into that task
- Immediate-command strip gives a live 3-step directive (open/move/copy) for the current board state
- Current-context trail shows exactly where you are (lane + selected task) at all times
- Current-context strip includes one-click “Open selected task details” action for instant return to editor focus
- Board-freshness strip shows the latest logged update with relative age + timestamp at a glance
- Lane guide explains Now/Next/Blocked/Done semantics at a glance directly above the board
- Lane highlight flash gives immediate visual confirmation when tasks are saved/moved
- Lane color system (Now/Next/Blocked/Done) improves scan speed and visual polish
- Symbol-coded phase pill (■ blocked / ● executing / → ready / ○ setup) and lane-colored counters make board state legible at a glance
- Board-health strip summarizes execution state instantly (blocked/executing/ready/empty)
- TL;DR strip gives a one-line immediate directive from live board state
- Keyboard shortcut strip speeds first actions: `N` add task, `F` open first action, `C` copy brief
- Execution-progress chips highlight current phase (choose → execute → share) at a glance
- Progress hint line explains the immediate next action for the active progress phase
- Validation checklist controls persist with live progress count so checks are never lost on rerender/refresh
- Accessibility baseline: skip link, visible keyboard focus states, aria-live action feedback, reduced-motion support, and dialog semantics for task modal
- Action status line confirms control results (save/open/copy/import/export/reset)
- Buttons now give immediate visual tap/click feedback so control activation is always visible
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
