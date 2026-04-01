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

BetterCallClaude is installed through the Claude Desktop COWORK marketplace. Follow these steps carefully.

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

### Step 2: Open COWORK

1. In Claude Desktop, click on **"Cowork"** in the top navigation bar
2. This opens the COWORK workspace area

![Open COWORK](../assets/screenshots/01_open_claude_cowork.png)
*Access the COWORK workspace*

### Step 3: Click Customize

1. In the left sidebar, click **"Customize"**
2. This opens the customization and plugins area

![Click Customize](../assets/screenshots/02_click_customize.png)
*Open the Customize panel*

### Step 4: Click the + Next to Personal Plugins

1. Find the **+** button next to **"Personal plugins"** in the left panel
2. Hover over it to see the "Add plugin" tooltip

![Click Personal Plugins +](../assets/screenshots/03_click_personal_plugins_+.png)
*Click the + button to add a plugin*

### Step 5: Select Add Marketplace

1. From the dropdown menu, hover over **"Create plugin"** to reveal the submenu
2. Click **"Add marketplace"**

![Add Marketplace](../assets/screenshots/04_click_+_create_plugin_ADD_MARKET_PLACE.png)
*Select Add marketplace from the menu*

### Step 6: Enter Repository and Sync

1. In the **"Add marketplace"** dialog, enter the URL: `fedec65/bettercallclaude`
2. Click **"Sync"** to fetch the plugin

![Enter repository](../assets/screenshots/05_enter_the_repo_fedec65:bettercallclaude.png)
*Enter the BetterCallClaude repository*

### Step 7: Click the Personal Tab

1. The **Directory** will open showing available plugins
2. Click the **"Personal"** tab to view your personal marketplace plugins

![Personal tab](../assets/screenshots/06_Click_Personal.png)
*Switch to the Personal tab in the Directory*

![Personal tab highlighted](../assets/screenshots/07_click_personal.png)
*Personal tab location*

### Step 8: Install BetterCallClaude

1. Find **Bettercallclaude** in the Personal plugins list
2. Click the **+** button on the plugin card to install it

![Install plugin](../assets/screenshots/08_click_+.png)
*Click + to install BetterCallClaude*

### Step 9: Grant MCP Server Permissions

1. A permissions dialog will appear warning that the plugin includes local MCP servers
2. Review the information and click **"Continue"** to grant the necessary permissions

![Grant permissions](../assets/screenshots/09_click_continue.png)
*Grant MCP server permissions*

### Step 10: Access Plugin Settings

1. After installation, you'll see Bettercallclaude listed under Personal plugins
2. Click the **gear wheel** icon on the plugin card to access settings

![Plugin settings](../assets/screenshots/10_click_the_gear_wheel.png)
*Click the gear wheel to configure*

### Step 11: Click Connectors

1. The plugin details page will open showing Skills, Agents, and Hooks
2. In the left sidebar, click **"Connectors"** to view the MCP servers
3. These are your data pipelines to Swiss legal databases

![Plugin details](../assets/screenshots/11_you_should_see_this_page_click_connectors.png)
*Plugin details page - click Connectors*

### Step 12: Verify All Connectors Are Allowed

1. You should see **6 connectors** listed in the left panel
2. For each connector, ensure the permission is set to **"Always allow"**
3. The tools should show checkmarks indicating they are enabled

![Connectors list](../assets/screenshots/12_make_sure_connectors_are_all_allowed.png)
*Verify all 6 connectors are present and allowed*

### Available Connectors Reference

You should see these **6 connectors**:

| Connector | Purpose |
|-----------|---------|
| `bettercallclaude-entscheidsuche` | Court decisions search |
| `bettercallclaude-bge-search` | Federal Supreme Court (BGE) lookup |
| `bettercallclaude-legal-citations` | Citation validation & formatting |
| `bettercallclaude-fedlex-sparql` | Federal legislation database |
| `bettercallclaude-onlinekommentar` | Legal commentaries |
| `bettercallclaude-ollama` | Local AI for privacy-sensitive work |

### Ollama (Optional)

If you have Ollama installed on your computer, the Ollama MCP connects automatically. This allows you to use local AI models for privacy-sensitive legal work.

---

### Post-Installation Setup

**Close and reopen BetterCallClaude** — this empties the cache and ensures the new MCPs are loaded properly.

Then run the setup command in COWORK to verify MCP server connections:

```
/bettercallclaude:setup
```

This command will:
- Verify all MCP servers are connected
- Configure default settings
- Display your available capabilities

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
> - All 6 connectors show in the list
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
