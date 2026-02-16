# Mission Control (Usable Workboard)

Mission Control is now a **functional execution board**, not a static mock.

## What works now

- Editable task board with 4 lanes: **Now / Next / Blocked / Done**
- Click any task card to open full detail editor
- Update status, priority, owner, link, and definition-of-done
- Add/delete tasks
- Copy a generated **execution brief** from live board state
- Add timeline/feed updates
- Export/import board JSON
- Persist board changes in browser `localStorage`
- Reset back to baseline `state.json`
- **10-second workflow map** at top to orient Plan → Edit → Unblock → Share instantly
- Quick-navigation chips jump directly to Workboard, Task details, Strike desk, and Recent updates
- Action status line confirms control results (save/open/copy/import/export/reset)
- Execution flow controls: pull top Next → Now, unblock top Blocked → Next, and one-click lane moves from task editor
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
