← [Back to Main Page](../README.md)

---

# Updating BetterCallClaude Plugin

> **Keep your plugin up to date with the latest features and improvements**

---

## How Cowork Plugin Updates Actually Work

Cowork's plugin system has **two independent layers**. Understanding the difference makes the update choice obvious.

---

## Layer 1 — The Marketplace Catalog

A **marketplace** is a Git repository whose `.claude-plugin/marketplace.json` lists which plugins exist and what version each is at. For you, the marketplace is `fedec65/bettercallclaude` itself.

Cowork keeps a **local cached copy** of that `marketplace.json`. Until that cache is refreshed, Cowork does not even know that a newer version exists.

### What refreshes the catalog?

| Action | What It Does | Result |
|--------|-------------|--------|
| **Manual Sync** (Sync button on the marketplace row) | Git-fetches the marketplace repo → re-reads `marketplace.json` → updates the local catalog | Installs **nothing**. Cheap, instant, safe. |
| **Auto-update marketplace** (toggle in the ⋯ menu) | Same as Manual Sync, but Cowork does it automatically — once on every app start, and periodically while running | Equivalent effect, just hands-off. |

> 💡 **Key insight**: Layer 1 only updates the *catalog*. It tells Cowork "version 4.5.0 exists." It does not download or install anything.

---

## Layer 2 — The Installed Plugin

Separately, for each plugin you have installed, Cowork tracks the **version you're actually running**. Your installed version does **not** change until you click **"Update plugin"** on that specific plugin.

The "Update plugin" button only becomes meaningful **after** the catalog has been refreshed to advertise a newer version (Layer 1).

### What "Update plugin" does

1. Downloads the plugin sub-directory at the version the catalog currently advertises
2. Validates it against Cowork's plugin validator
3. Swaps it in
4. Prompts for any new `userConfig` keys if the schema changed

> ⚠️ This is the **only** action that actually changes what code runs on your machine.

---

## What's New since v4.6.1

The current release is **v4.9.6**. Highlights since v4.6.1, grouped by theme:

### Goal-loop verification (v4.9.0)

- **`/legal-goal`** — declare a measurable goal for a work session (e.g. "every citation verified against its source").
- **`/legal-loop`** — runs an iterative worker → judge loop until the goal is met: default max 5 iterations (hard cap 20), stops after 2 stagnant rounds, the judge never builds what it judges, and an honest `NOT MET` always beats a false pass. The full trail is written to `bcc-output/loops/`. Built-in profiles include `citations-clean`, `draft-passes-gate`, `adversarial-converge`, `nda-batch-clean`, `reg-watch`, and `timeline-sourced`.
- Walkthrough: [Mastering Workflows §5.5](./mastering-workflows.md).

### Sourced case timelines (v4.9.5)

- **`/legal-timeline`** — builds a chronology in which **every event carries provenance**, events are labeled undisputed / alleged / contested, date conflicts keep **both** dates, gaps of 30+ days are flagged, and deadlines are computed under ZPO Art. 142–149 and BGG Art. 46 / 100–101 (cantonal holidays included). Verjährung deadlines are always marked "indicative", never definitive. Outputs land in `bcc-output/timeline/` as `timeline.md` / `.html` / `.docx`; `--merge` updates an existing timeline in place.
- Walkthrough: the [Case Chronology scenario](./scenarios/case-chronology.md).

### Citation content gate

- `/validate` now verifies not just that cited sources **exist**, but that their **content supports the claim** (citation-content-verify). Each citation receives a MATCH / PARTIAL / MISMATCH / UNVERIFIED / SKIPPED verdict; UNVERIFIED and MISMATCH block delivery. Strict mode downgrades to existence-only checks, marked `(privacy-gated)`.

### Firm playbook and NDA triage (v4.8.0)

- **`/start`** — guided first-run setup that also creates your local playbook `bettercallclaude.local.md` from DE/FR/IT/EN templates.
- **`/nda-triage`** — rapid NDA review, single file or batch, rating each clause GREEN / YELLOW / RED and flagging Art. 160 ff. OR validity limits, Lugano forum clauses, and zwingendes Recht overrides.
- `/draft` now classifies deviations from your playbook as *conforme*, *accettabile*, *negoziare*, or *inaccettabile*.
- Walkthrough: the [NDA Triage scenario](./scenarios/nda-triage.md).

### Deliverables as files (v4.8.1)

- Long outputs are written to `bcc-output/YYYY-MM-DD-<slug>/` as numbered phase files plus a `sources.md`; the chat keeps only a 3–5 line summary pointing to the files. The output folder is configurable in the playbook.

### Diagnostics

- **`/doctor`** — one-command health check of all 9 MCP connectors and your configuration. The old `/setup` still works as a deprecated alias that now calls `/start`.

### Privacy fixes (v4.6.2 and v4.9.6)

- **v4.6.2** — the privacy config can now only raise, never lower, severity; Bash path-exfiltration checks; a strict-mode enforcement fix; documented evasion limits.
- **v4.9.6** — fixes a silent failure where an unquoted `${CLAUDE_PLUGIN_ROOT}` disabled the privacy hook whenever the plugin path contained spaces. If your BetterCallClaude lives under a path with spaces, update for this alone. Details: [Privacy & Responsibility](./appendix/privacy-responsibility.md).

### Still current from v4.6.1

- **`/legal-5step`** — the full 5-phase framework as one sequential pipeline: Intake → Research → Strategy → Adversarial → Draft, with quality gates at Steps 3 and 4. Flags: `--short`, `--medium`, `--long`, `--no-summary`, `--stop-after`, `--lang`, `--canton`.
- **`/privacy`** — check and switch privacy mode (`strict` / `balanced` / `cloud`).

---

## What the Combinations Do

| Catalog Refresh | Plugin Update | Result |
|-----------------|---------------|--------|
| Manual sync | Manual click | You are in full control. Nothing changes unless you do **both** steps. Safest; recommended if you want to pin versions. |
| Auto-update marketplace | Manual click | Cowork silently knows about new versions, but won't install them. You get a visible "Update" indicator. **Sweet spot for most users** — zero friction on discovery, explicit consent on install. |
| Manual sync | *(no auto on the plugin — there is no "auto-update plugin")* | Same as above; just means you also have to remember to hit Sync. |
| Auto-update marketplace | Auto | **Not exposed in the UI.** Plugin installation is always an explicit click. |

---

## Recommended Settings for BetterCallClaude

### Turn ON "Sync automatically" for the marketplace

Since `fedec65/bettercallclaude` is your own plugin — you're the only publisher, and it has no third-party supply-chain risk — auto-sync is safe and convenient. You'll get a visible "Update" cue when a new release ships, without any manual Sync step.

### Leave "Update plugin" as manual

After each release, click **Update** once, answer any new `userConfig` prompt, and you're on the new version. This gives you a chance to:

1. **Read the CHANGELOG** first
2. **Test in a controlled moment** rather than mid-session

If a `userConfig` schema change happens mid-session, manual plugin update is your protection. Auto marketplace refresh is harmless — no code runs as a result of a catalog fetch.

---

## Step-by-Step: Enable Auto-Sync

### Step 1: Open Customize

In Cowork, click **"Customize"** in the left sidebar.

![Click Customize](../assets/screenshots/update_v2_01_customize.png)
*Open the Customize panel*

---

### Step 2: Browse Plugins

Click the **+** next to **"Personal plugins"**, then select **"Browse plugins"**.

![Browse plugins](../assets/screenshots/update_v2_02_browse_plugins.png)
*Open the plugin browser*

---

### Step 3: Enable "Sync automatically"

1. Find the **Bettercallclaude** plugin card
2. Click the **three dots (⋯)** menu on the right
3. Toggle **"Sync automatically"** to **ON**

![Toggle Sync automatically](../assets/screenshots/update_v2_03_sync_automatically.png)
*Enable automatic marketplace catalog refresh*

**What this does:**
- Cowork will periodically fetch the latest `marketplace.json` from `fedec65/bettercallclaude`
- When a new version is published, Cowork will know about it automatically
- **Nothing is installed** — you just get an "Update" indicator

---

### Step 4: Update When Available

When a new version is available, go back to the plugin overview and click the **"Update"** button.

![Update button](../assets/screenshots/update_v2_04_plugin_overview.png)
*Click Update to install the new version*

**What happens:**
- Cowork downloads and validates the new plugin version
- If the `userConfig` schema changed, you'll be prompted for any new settings
- The new version is swapped in immediately

---

## Post-Update Steps

After updating, we recommend:

1. **Restart COWORK**: Close and reopen the workspace to ensure all changes take effect
2. **Verify connectors**: Check that all 9 MCP connectors are still enabled
3. **Run setup and diagnostics**: Type `/bettercallclaude:start` to verify configuration, then `/bettercallclaude:doctor` for a full connector health check
4. **Test a quick query**: Try a simple citation lookup to confirm functionality

---

## Troubleshooting Updates

### Issue: "Update" button doesn't appear

**Cause**: The marketplace catalog hasn't been refreshed yet, so Cowork doesn't know a newer version exists.

**Solution**:
- If auto-sync is ON: wait a moment, or restart Cowork (it fetches on startup)
- If auto-sync is OFF: click the ⋯ menu → **"Check for updates"** to force a catalog refresh

### Issue: Update fails or stalls

**Solution**:
1. Close Cowork completely
2. Reopen and try again
3. If it persists, remove and reinstall the plugin. If the marketplace catalog itself seems stuck on a stale version, force a manual sync (⋯ menu → "Check for updates"), or remove and re-add the marketplace to rebuild the cached catalog.

### Issue: Connectors missing after update

**Solution**:
1. Go to the plugin settings (gear icon)
2. Click **Connectors** in the left sidebar
3. Ensure all 9 connectors are set to **"Always allow"**

---

## Edge Cases Worth Knowing

### Downgrades

If `marketplace.json` drops from 4.4.0 back to 4.3.0 (e.g., you revert a release), auto-sync will pick up the lower version on next fetch, and the "Update" button will offer the older version. Nothing warns you — verify the version number before clicking Update.

### Cache staleness on fresh install

If you install BetterCallClaude on a new machine and hit "Install", Cowork uses whatever its current cached `marketplace.json` says. On a fresh install this is freshly fetched, so you always get the latest version at install time.

### Zip uploads bypass the marketplace

If you ever install BetterCallClaude via a manual ZIP upload (e.g., for beta testing), the plugin is **pinned to that exact zip** regardless of what's in the marketplace. You'd have to uninstall and reinstall from the marketplace to rejoin the automatic update flow.

---

## ✅ Update Checklist

- [ ] Auto-sync is enabled on the `fedec65/bettercallclaude` marketplace
- [ ] I understand that auto-sync only refreshes the catalog — it does not install updates
- [ ] I will click "Update" manually when a new version is available
- [ ] After updating, I restart COWORK
- [ ] After updating, I verify all 9 connectors are enabled
- [ ] After updating, I run `/bettercallclaude:start` and `/bettercallclaude:doctor` to confirm connectivity

---

*Last updated: August 2026 — v4.9.6*
