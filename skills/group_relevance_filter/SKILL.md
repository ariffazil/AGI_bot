# group_relevance_filter.md

## Purpose

MUCA-style relevance filter for Telegram groups.  
Bot decides "should I respond?" before calling the LLM.  
Humans don't need to use @mention.

---

## Trigger Conditions

Respond if message contains ANY of:

| Category | Indicators | Examples |
|----------|-------------|----------|
| **Question** | `?`, `why`, `how`, `apa`, `kenapa`, `who`, `where`, `when` | "apa itu F1?", "how do I..." |
| **Request** | `bantu`, `tolong`, `carikan`, `buatkan`, `tolong`, `help`, `please` | "tolong saya...", "bantu cari..." |
| **arifOS keywords** | `arifOS`, `arif`, `kernel`, `floor`, `apex`, `f1`, `f13`, `omega` | " apa tu arifOS?" |
| **Problem/Error** | `error`, `bug`, `problem`, `tak jadi`, `failed`, `rosak` | "system error...", "tak jalan" |
| **Code/Technical** | `{`, `}`, `def `, `function`, `code`, `syntax`, `python`, `javascript` | "def init_anchor" |

## Silence Conditions

DO NOT respond if:

| Category | Indicators | Examples |
|----------|-------------|----------|
| **Casual chat** | Just greeting, no question | "okay", "siap", "okies" |
| **User-to-user** | No arifOS keywords, no question mark | Two humans talking |
| **Bot command** | Not directed at bot | Bot talking to another bot |
| **Acknowledge** | Just reaction/emoji | "👍", "okay je" |

---

## Implementation Pattern

```
Message arrives
  → Check: is question? → YES → respond
  → Check: is request? → YES → respond
  → Check: has arifOS keywords? → YES → respond
  → Check: has technical content? → YES → respond
  → DEFAULT → stay silent
```

---

## Note

This is a relevance gate, not a content filter.  
All responses still go through normal APEX pipeline.  
This only decides WHETHER to call the LLM, not what to say.

---

**Version:** 2026.03.30  
**Framework:** MUCA (Multi-User Chat Assistant)  
**Author:** Muhammad Arif bin Fazil (arifOS)