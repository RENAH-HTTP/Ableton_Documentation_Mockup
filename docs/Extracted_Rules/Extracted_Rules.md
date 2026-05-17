# Rules for Writing
1. American English — No British spellings (colour → color, grey → gray, programme → program, etc.)
2. No marketing language — No exciting, powerful, innovative, seamless, revolutionary, game-changing, etc.
3. User-facing language — No developer jargon (implemented, refactored, backend, API call, hotfix, deprecated, etc.)
4. Do not start with I/We — Lead with the subject, the feature, or the action.
5. UI element capitalisation — Named UI elements are proper nouns (Arrangement View, Group Track, Auto Filter, Correction, Formant, etc.)
6. Acronym capitalisation — MIDI, MPE, CPU, GPU, VST, AU, AAX, DAW, LFO, ADSR, OSC are always all-caps.
7. No contractions — Use full forms: don't → do not, can't → cannot, it's → it is, etc.
8. Software name capitalisation — Live (the software) and version refs like Live 12 are always capitalised.
9. Grammar: allows/enables to — allows to and enables to are grammatically wrong. Use allows you to or lets you.
10. Paragraph length — Max 4 sentences per paragraph. (Not enforced in Free mode)
11. Passive voice — Avoid was added, has been updated, can be accessed. Use active voice.
12. Bug fix structure (Bug Fix mode) — Must describe both: what broke AND what now works.
13. Release note structure (Release Note mode) — Must lead with what the user can now DO.
14. Minimize words — Cut simply, just, easily, obviously, of course, clearly — they make tasks sound trivial.
15. Weak sentence opener — Avoid starting sentences with There is/are or It is. Lead with the real subject.
16. Redundant phrasing — in order to → to, due to the fact that → because, at this point in time → now, etc.
17. Filler phrases — Cut please note, note that, it is worth noting, as you can see, etc.
18. Double spaces — Single space between words and after punctuation.
19. Trailing ellipsis — ... at the end of a sentence implies an unfinished thought.
20. Avoid etc. — Complete the list or write and
21. Parameter Values - place parameter values in double quotes. 100% is "100%".

**Release Note Only**
1. Release note structure — must describe what the user can now DO (looks for: "can now", "lets you", "allows you", "use", "select", "access", etc.)

# Bug Fix Rules

1. Always lead with "Fixed" — "Fixed an issue where...", "Fixed a bug where...", "Fixed a crash that occurred when..."
2. Platform-specific bugs — name the platform first. "Fixed an issue on macOS where...", "Fixed an issue on Windows where..."
3. Describe the trigger — what action or condition caused the bug. Be specific.
4. Describe the outcome — what now works. Can be a second sentence: "X now Y."
5. Passive voice IS allowed here — "Fixed an issue where X was not Y" is the standard form. The linter skips passive checks in Bug Fix mode.
6. Use bullet points for multiple related fixes in the same release.
7. No crash without a trigger — "Fixed a crash" alone is not enough. State what caused it.
8. All standard rules still apply — American English, UI element caps, no marketing, no dev jargon, no contractions, acronym caps, etc.