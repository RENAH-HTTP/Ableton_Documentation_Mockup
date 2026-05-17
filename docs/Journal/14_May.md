# Thursday, 14 May 

## Situation
Release notes have different rules depending on what type of change it is. Updates, fixes, bugs — past tense, passive voice. Platform-specific stuff — you lead with the platform name. "On Windows,...", "On macOS,...". 

Also ran into this example: "On Windows, it is now possible to navigate Live's browser forward and back with the mouse browser navigation buttons. This feature works when Live's browser is in focus." — wait, isn't browser a UI element? Should that be Browser? 

## Task
Get the tense/voice rules straight for each release note type. Figure out if browser counts as a UI element or not.

## Action
Tested a few release note entries against the patterns. Updates and bugs consistently use past passive — "was added", "was fixed", "has been updated". Platform entries always open with "On [Platform]:" and use present tense after. Two different contexts, two different rules.

For browser — open question. It behaves like a named component. Probably should be capitalized. Ask the team.

Updated the linter to reflect what I learned — added checks for past tense passive in fix/update entries and the "On [Platform]:" prefix pattern. Also created a dedicated Bug Fix Rules section at the bottom of this report next to the main rules.

## Result
Two rules:

1. Updates / fixes / bugs — past tense, passive voice.
   "The issue was fixed where...", "A new option was added..."

2. Platform-specific updates — lead with "On [Platform]:"
   Present tense follows. "On macOS, it is now possible to..."

3. Browser — probably a UI element. Probably Browser. Not confirmed yet.
