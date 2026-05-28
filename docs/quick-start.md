← [Back to Main Page](../README.md)

---

# Part 1: Quick Start

> **Get your first success in 15 minutes**

## What You'll Achieve

By the end of this section, you will be able to:

- Verify BetterCallClaude is working
- Look up your first BGE citation
 - Run your first legal research
 - Set up your workspace for a new matter

**⏱️ Estimated time: 15 minutes**

---

## 1.1 Prerequisites

Before you begin, ensure you have:

- ✅ A COWORK account with internet access
 - ✅ Basic familiarity with Swiss legal citations (BGE/ATf/DTF format)

---

## 1.2 Installation in COWORK

BetterCallClaude is installed through the Claude Desktop COWORK marketplace. The process has **two distinct phases**:

1. **Phase 1 — Add the marketplace catalog** (makes BetterCallClaude visible)
2. **Phase 2 — Install the plugin** (downloads the actual code)

> 🌙 **A Note on Interface Changes**  
> Anthropic has a peculiar habit of redesigning the COWORK interface while the rest of us are sleeping. If these instructions don't match what you see on screen, don't worry—you're not going crazy. The menu items have simply taken a midnight stroll to new locations. We update this documentation as fast as humanly possible, but the UI may occasionally outpace us. When in doubt, look for buttons that sound similar to what we describe here.

### Prerequisites

Before installing, ensure you have:
- ✅ Claude Desktop installed on your computer
- ✅ Internet connection active
- ✅ Network access enabled (see Step 1)

### Step 1: Enable Network Access

First, enable network permissions in Claude Desktop:

1. Open Claude Desktop
2. Go to **Settings** → **Capabilities**
3. Toggle **"Allow network egress"** to ON

![Enable network access](../assets/screenshots/1_enable_network_access.png)
*Enable network egress in Claude Desktop Settings*

### Step 1.5: Windows 11 Home Setup (Windows Users Only)

If you're using **Windows 11 Home**, there's one extra step before continuing. Claude COWORK needs the Virtual Machine Platform and Windows Subsystem for Linux to run properly — these aren't enabled by default on Windows 11 Home.

Don't worry, this is a quick fix! Choose one of the options below:

#### Option A — PowerShell (Recommended, ~2 minutes)

1. Open **PowerShell as Administrator** (right-click PowerShell → "Run as administrator")
2. Run these two commands:

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
wsl --install
```

3. **Restart your computer** when prompted

#### Option B — Windows Settings (~3 minutes)

1. Open **Settings → System → Optional Features**
2. Click **"More Windows features"** at the bottom
3. Check both boxes:
   - ☑️ Virtual Machine Platform
   - ☑️ Windows Subsystem for Linux
4. Click **OK** and **restart your computer**

After restarting, come back here and continue with Step 2. You only need to do this once!

> 💡 **Seeing "VM service not running"?** This means the above features aren't enabled yet. Enable them and restart, then try the installation again.

---

### Phase 1 — Add the Marketplace Catalog

A **marketplace** is a catalog that tells COWORK which plugins exist and what versions are available. Adding the `fedec65/bettercallclaude` marketplace does **not** install anything yet — it simply makes the plugin visible in your directory.

#### Step 2: Open the Plugin Directory

1. In Claude Desktop, click **"Cowork"** in the top navigation bar
2. In the left sidebar, click **"Customize"**

![Open Customize](../assets/screenshots/install_01_customize.png)
*Open the Customize panel*

#### Step 3: Add a Marketplace

1. Click the **+** button next to **"Personal plugins"**
2. From the dropdown, select **"Add marketplace"**

![Click the + sign](../assets/screenshots/install_02_plus_sign.png)
*Click the + button to reveal options*

![Add marketplace](../assets/screenshots/install_03_add_marketplace.png)
*Select "Add marketplace" from the dropdown*

#### Step 4: Enter the Repository and Sync

1. In the **"Add marketplace"** dialog, enter the repository: `fedec65/bettercallclaude`
2. Click **"Sync"** to fetch the catalog

![Enter repository and sync](../assets/screenshots/install_04_enter_repo_sync.png)
*Enter the repository URL and click Sync*

#### Step 5: Switch to the Personal Tab

1. The **Directory** will open showing available plugins
2. Click the **"Personal"** tab to view plugins from your marketplace

![Click Personal tab](../assets/screenshots/install_05_click_personal.png)
*Switch to the Personal tab in the Directory*

#### Step 6: Enable Auto Sync (Recommended)

1. Find the **bettercallclaude** marketplace row (shown under "Local uploads")
2. Click the **⋯** (three dots) menu on the marketplace row
3. Toggle **"Sync automatically"** to ON

![BetterCallClaude 3-dots menu](../assets/screenshots/install_06_bettercallclaude_3dots.png)
*Click the three-dots menu on the marketplace row*

![Enable auto sync](../assets/screenshots/install_07_sync_automatically.png)
*Toggle "Sync automatically" to ON*

> 💡 **Why enable Auto Sync?** This keeps your marketplace catalog up to date. COWORK will periodically check for new versions and show an **Update** button when one is available. The plugin itself does not auto-update — you always choose when to click **Update**. For details, see [Updating the Plugin](./updating-plugin.md).

---

### Phase 2 — Install the Plugin

Now that the marketplace catalog is added and auto-sync is enabled, install the actual plugin.

#### Step 7: Install BetterCallClaude

1. In the **Personal** tab, find the **Bettercallclaude** plugin card
2. Click the **+** button on the card to install

![Click + to install plugin](../assets/screenshots/install_08_click_plus_plugin.png)
*Click the + button on the BetterCallClaude plugin card*

#### Step 8: Grant MCP Server Permissions

1. You'll see a toast notification: *"Bettercallclaude is installed and ready to use."*
2. A dialog will appear warning that the plugin includes local MCP servers
3. Click **"Continue"** to grant permissions

![MCP permissions dialog](../assets/screenshots/install_09_mcp_continue.png)
*Click Continue to allow the MCP servers*

#### Step 9: Open Plugin Settings

1. Click the **gear wheel** icon on the Bettercallclaude plugin card
2. This opens the plugin details page

![Click gear wheel](../assets/screenshots/install_10_gear_wheel.png)
*Click the gear wheel to open plugin settings*

#### Step 10: Navigate to Connectors

1. In the left sidebar of the plugin details page, click **"Connectors"**
2. These are your data pipelines to Swiss legal databases

![Click Connectors](../assets/screenshots/install_11_click_connectors.png)
*Click Connectors in the left sidebar*

#### Step 11: Set All Connectors to "Always Allow"

1. You should see **9 connectors** listed in the left panel
2. Click each connector and set its permission to **"Always allow"**
3. This ensures Claude can use the tools without asking every time

![Set Always Allow](../assets/screenshots/install_12_always_allow.png)
*Set each connector's permission to "Always allow"*

### Available Connectors Reference

You should see these **9 connectors**:

| Connector | Purpose |
|-----------|---------|
| `bettercallclaude-entscheidsuche` | Court decisions search |
| `bettercallclaude-bge-search` | Federal Supreme Court (BGE) lookup |
| `bettercallclaude-legal-citations` | Citation validation & formatting |
| `bettercallclaude-fedlex-sparql` | Federal legislation database |
| `bettercallclaude-onlinekommentar` | Legal commentaries |
| `legal-persona` | Swiss-law document intelligence (drafting, strategy, analysis) |
| `tas-jurisprudence` | CAS/TAS sports arbitration decisions |
| `swiss-caselaw` | Case law, citation graphs, appeal chains |
| `ollama` | Local AI for privacy-sensitive work |

### Ollama (Optional)

If you have Ollama installed on your computer, the Ollama MCP connects automatically. This allows you to use local AI models for privacy-sensitive legal work.

---

### Post-Installation Setup

**Close and reopen BetterCallClaude** — this empties the cache and ensures the new MCPs are loaded properly.

Then run the setup command in COWORK to verify MCP server connections:

```
/bettercallclaude:setup
```

This command checks connectivity for all 9 MCP servers and displays their status. No additional configuration is needed — 8 remote servers connect automatically via HTTP, plus 1 via SSE.

**Optional: Check your privacy mode**
```
/bettercallclaude:privacy
```
This shows your current privacy mode (`strict`, `balanced`, or `cloud`). Most users should keep the default `balanced` mode.

### Verification

To confirm everything is working, try typing:

```
Hello, are you available?
```

You should receive a response confirming BetterCallClaude is active and ready.

---

> ⚠️ **Installation issues? Check:**
> - Network egress is enabled (Step 1)
> - **Windows 11 Home:** VM Platform and WSL are enabled (Step 1.5)
> - Repository name is exactly `fedec65/bettercallclaude`
> - All 9 connectors show in the list
> - Each connector is set to "Always allow"

---

## 1.3 Your First Citation Lookup

 Let's verify BetterCallClaude is working by looking up a real Swiss Federal Supreme Court decision.

### What to Type

 In COWORK, simply type:```
/bettercallclaude:cite BGE 147 IV 73
```### What You'll See

 BetterCallClaude will return:

```📄 **BGE 147 IV 73**

**Court**: Federal Supreme Court
 Switzerland
**Chamber**: IV (Criminal Law)
**Date**: 2021
 **Language**: German

**Summary**: [Brief summary of the case]

**Full Text**: [Link to full decision]
```

### Why This Matters

 This 10-second task would take 10+ minutes manually if you had to:
 - Navigate to the Federal Supreme Court website
 - Search for the specific citation
 - Find the correct language version
 - Locate the relevant passage

 BetterCallClaude does all of this instantly, accessing multiple databases simultaneously.

---

> ⚠️ **No results? Try this:**
> - Check your citation format: Use `BGE 147 IV 73`, not "147 IV 73"
 (without BGE)
 or "BGE147IV73" (no spaces)
 - Try German terms if English doesn't work: "Bundesgericht" instead of "Federal Court"
 - Use broader search terms, then narrow down
 - Verify the decision exists at entscheidsuche.ch if official sources fail

---

## 1.4 Your First Legal Research

 Now let's run a simple legal research query.### What to Type

```
/bettercallclaude:research Art. 97 OR contractual liability limitation period```### What You'll See

 BetterCallClaude will search across:
 - 📚 BGE/ATF/DTF decisions (Federal Supreme Court)
 - 📋 Cantonal court decisions
 - 📖 Legal commentaries (OnlineKommentar.ch)
 - 📄 Statutory provisions (Fedlex)

### Understanding the Response

 The response typically includes:

1. **Relevant Precedents**: Key cases that interpret Art. 97 OR
2. **Statutory Analysis**: The text of Article 97 itself
3. **Related Provisions**: Other relevant articles
4. **Practical Guidance**: How courts apply the law

### Key Takeaway

 **AI does the heavy lifting, you validate.** You always have final responsibility to verify citations and assess relevance.

---

## 1.5 Setting Up Your Workspace in COWORK

### Why a Dedicated Directory Matters

BetterCallClaude uses **context persistence** — it remembers your case across sessions. This only works when you work in a dedicated directory per matter.

**Benefits:**
- **🧠 Memory**: BetterCallClaude "remembers" your case context across sessions
- **📁 Organization**: All related files in one place
- **🔄 Resume**: Pick up where you left off days or weeks later without re-explaining

### How to Create a Case/Matter Directory

In COWORK, create a new folder for each matter:

```
📁 2024-001_Smith_v_AG/    (Year-Number_ClientName_MatterType)
    ├── 📄 CLAUDE.md          # ⚠️ CRITICAL: Must be in root of this folder
    ├── 📄 contracts/         # Related documents
    ├── 📄 correspondence/    # Emails, letters
    ├── 📄 research/          # Research notes
    └── 📄 drafts/            # Working drafts
```

---

### The CLAUDE.md File: Your Persistent Case Memory

#### What is CLAUDE.md?

`CLAUDE.md` is a **markdown file that BetterCallClaude automatically reads at the start of every conversation** in that directory. Think of it as your "case briefing document" that the AI reads before every interaction.

#### Why is it Important?

| Without CLAUDE.md | With CLAUDE.md |
|-------------------|----------------|
| You re-explain the case every session | AI already knows the context |
| Inconsistent advice across sessions | Coherent, building advice |
| Wasted time on background | Jump straight to substantive work |
| Risk of missing key details | All facts documented and referenced |

#### Why Must It Be in the Root Directory?

**Claude Code looks for `CLAUDE.md` in the root of your current working directory.** This is a built-in behavior:

1. When you open a folder in COWORK, that folder becomes your "working directory"
2. At the start of each conversation, Claude Code checks: *Is there a `CLAUDE.md` file here?*
3. If found → It reads the file and uses it as context
4. If not found → You start with no case context

**This means:**
- ✅ Put `CLAUDE.md` in the root of your matter folder
- ❌ Don't bury it in a subfolder (Claude won't find it)
- ❌ Don't name it differently (only `CLAUDE.md` is recognized)

---

### What to Put in CLAUDE.md

```markdown
# Case: Smith v. AG

## Client
- **Name**: John Smith
- **Type**: Individual
- **Contact**: john.smith@email.com

## Opposing Party
- **Name**: AG Corporation
- **Type**: AG (Swiss corporation)
- **Industry**: Manufacturing

## Matter Summary
Contract dispute arising from commercial lease agreement dated 15 March 2023. Client claims AG violated exclusivity clause by soliciting competitor quotes.

## Key Facts
1. 5-year commercial lease signed 15.03.2023
2. Exclusivity clause: 2km radius, retail products only
3. AG approached competitor (Müller GmbH) for quote in September 2024
4. Client discovered competitor quote in October 2024
5. No written termination yet

## Legal Issues
- Contractual liability (Art. 97 OR)
- Damages calculation (Art. 99 OR)
- Potential injunctive relief
- Jurisdiction: Zurich Commercial Court

## Key Documents
- Commercial lease agreement (15.03.2023)
- Correspondence with AG (various dates)
- Competitor quote from Müller GmbH (10.2024)
- Client's internal notes

## Status
- **Phase**: Initial assessment
- **Next Steps**: Legal opinion on breach and damages
- **Deadline**: Client meeting 20.01.2025
```

---

### Example: Minimal CLAUDE.md for Quick Start

For your first matter, start simple:

```markdown
# Matter: [Brief description]

## Parties
- **Plaintiff/Client**: [Name and role]
- **Defendant/Opposing Party**: [Name and role]

## Core Issue
[One or two sentences describing the legal question]

## Key Documents
- [List important documents with dates]

## Status
- **Phase**: [Current phase]
- **Next**: [What you're working on now]
```

---

### Why CLAUDE.md is Critical for Your Legal Practice

**CLAUDE.md is your persistent case memory.** Without it, every conversation with BetterCallClaude starts from zero — you must re-explain the parties, the facts, the legal issues, and the current status. With it, BetterCallClaude already understands your case context the moment you start a conversation.

**The one-case-one-directory rule:** Each legal matter deserves its own directory, and each directory must have its own `CLAUDE.md` file in the root. This is not optional — it's how BetterCallClaude knows which case you're working on.

```
📁 2024-001_Smith_v_AG/
    └── CLAUDE.md          ← BetterCallClaude reads THIS for this case

📁 2024-002_Mueller_v_GmbH/
    └── CLAUDE.md          ← BetterCallClaude reads THIS for this case
```

**When you open a directory in COWORK:**
- BetterCallClaude looks for `CLAUDE.md` in that directory's root
- It loads the file content as context before your first message
- All conversations in that directory benefit from that context

**If you forget CLAUDE.md:**
- BetterCallClaude has no memory of your case
- You waste time re-explaining background every session
- Advice may be inconsistent across conversations

---

> ⚠️ **Context Not persisting? Check:**
> - Are you in the correct directory? (Check your current working directory)
> - Does CLAUDE.md exist? (It should be in your matter folder)
> - Is CLAUDE.md properly formatted? (Use proper markdown headers)
> - Did you save after creating/editing? (BetterCallClaude reads it at conversation start)

---

## ✅ Quick Start Checklist

Before moving on, verify:

- [ ] BetterCallClaude is installed in COWORK
- [ ] I can run `/bettercallclaude:cite BGE 147 IV 73` successfully
- [ ] I understand the response structure
- [ ] I have a dedicated directory for my matter
- [ ] I have created a CLAUDE.md file with basic case information

---

**🎉 Congratulations! You're ready to understand your AI assistant better.**

**Next**: [Understanding Your AI Assistant](./understanding-ai.md) →
