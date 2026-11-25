---
created: 2026-11-21
---
Espresso cup with measuring lines 
Wallet 


Add tags to Worship site for filtering 

{
  "name": "Inkling 2 Mini Research",
  "trigger": {
    "type": "cron",
    "cron": "0 9 * * *",
    "tz": "America/Los_Angeles"
  },
  "action": {
    "type": "prompt",
    "prompt": "This repo consists of scripts and code for running Inkling 2 Mini locally on this PC. Look for findings/advancements/releases over the past 24 hours (things like Reddit, Twitter, forums, official releases like Unsloth and llamacpp, etc) that would benefit my Inkling performance, context size, speed, thinking budget, etc using the Browse tool. Then, using gmail.com via Browse, email syguy2003@outlook.com a report of your findings.",
    "to": { "session": "ses_..." }
  }
}