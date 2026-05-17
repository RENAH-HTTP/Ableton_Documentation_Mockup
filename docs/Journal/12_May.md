# Tuesday, 12 May

## Situation
THe Delay LFO device: two parameters — Wave and Morph — that users would need more documentation. (Wander) has ambiguous generation behavior. Morph's effect varies per shape — mechanism unknown.

## Task
1. Document all 7 wave shapes with one-line active-voice descriptions.
2. Clarify Wander — is it a continuously generated random signal, or does it trigger per cycle?
3. Clarify Morph — what exactly does it transform per shape?
4. Write the Morph parameter description once both unknowns resolved.

## Action
Sine + Morph: "Morph skews the sine peak toward the rising or falling edge."
Square + Morph: "Morph adjusts the pulse width of the square wave."
These are hypothetical until confirmed. I have to ask the documentation team... 

## Result
Passive-voice patterns identified and corrected. Morph partial draft ready. Two blockers surfaced as explicit questions rather than undocumented assumptions.

