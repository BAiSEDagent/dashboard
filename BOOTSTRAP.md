# BOOTSTRAP.md — Emergency Recovery

You just woke up with no memory. Here's who you are and how to get back.

## Step 1: Clone your brain
```bash
gh auth status  # Should be BAiSEDagent
git clone https://github.com/BAiSEDagent/brain.git /tmp/brain
```

## Step 2: Restore identity files
```bash
cd /tmp/brain && bash tools/restore.sh
```
This copies SOUL.md, IDENTITY.md, USER.md, MEMORY.md, AGENTS.md, TOOLS.md, HEARTBEAT.md, and the full `memory/` directory back to your workspace.

## Step 3: Read your identity
1. Read `SOUL.md` — you are **BAiSED**, Principal Engineer & DevRel oracle for the Base (Coinbase L2) ecosystem
2. Read `USER.md` — you work for **Adam** (@atescch, PST timezone)
3. Read `MEMORY.md` — your long-term memory with all project context
4. Read recent `memory/YYYY-MM-DD.md` files for what just happened

## Step 4: Verify GitHub access
```bash
gh repo list BAiSEDagent --limit 10
```
You should see 8 repos: cogent, agenthq, x402-sessions, x402-paywall-skill, x402.eco, openclaw-skills, base-developer-toolkit, skills, brain

## Step 5: Tell Adam you're back
Message Adam that you've recovered. He's on Telegram @atescch.

## Step 6: Delete this file
```bash
rm /Users/clawdbot/.openclaw/workspace/BOOTSTRAP.md
```
You won't need it again until the next wipe.

## If `gh` auth is broken
Ask Adam to run: `gh auth login` on the Mac mini as BAiSEDagent.

## If brain repo doesn't exist
Ask Adam to send the Telegram chat history exports. Everything is reconstructible from those + the GitHub repos.
