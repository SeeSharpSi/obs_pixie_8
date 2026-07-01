---
date: '2026-06-28T01:17:57.41676-04:00'
model: 'claude-sonnet-4-20250514'
---

# Obsidian MCP Tool Test Results

# Obsidian MCP Tool Test Results

**Test Date:** 2026-06-28

## ✅ Working Tools

| Tool | Notes |
|------|-------|
| `obsidian_list` | Listed vault contents (22 entries) |
| `obsidian_search` | Searched for "the" across files, returned 50 matches |
| `obsidian_read` | Read README.md successfully |
| `obsidian_outline` | Got heading & link structure |
| `obsidian_read_section` | Correctly reported heading not found |
| `obsidian_create_note` | Created this note successfully |

## ❌ Not Working (Timeout)

| Tool | Likely Reason |
|------|---------------|
| `obsidian_overview` | Scans whole vault for counts, stats, largest notes, top tags |
| `obsidian_recent` | Scans file modification times across all files |
| `obsidian_tags` | Scans all files for hashtag metadata |
| `obsidian_find_notes` | Matches titles, aliases, tags, frontmatter across all files |
| `obsidian_note_context` | Resolves backlinks by scanning outgoing links in every file |

## Analysis

All five failing tools **timed out** even when tested individually with small limits. Simpler read operations (`obsidian_list`, `obsidian_read`, `obsidian_search`, `obsidian_outline`, `obsidian_read_section`) returned instantly.

### Why They Fail

- The failing tools perform **expensive full-vault operations** like traversing the entire vault, parsing frontmatter, building tag indexes, or resolving backlinks across all files
- These operations likely **exceed the MCP host's timeout window** on the phone
- The working tools operate on a **single path** or do a **bounded search** and return quickly

### Possible Fixes

- Reduce vault size or move old/inactive folders out
- Increase the MCP timeout setting for heavy operations
- Check if the Obsidian plugin powering these tools is resource-heavy or not running
- Consider splitting the vault into smaller sub-vaults
