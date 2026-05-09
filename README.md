https://justinsteinmetz.github.io/SOCIALCONTRACT/
# SOCIAL CONTRACT

**A civic simulation instrument for Grades 11–12.**

> The contract is not experienced equally by everyone asked to uphold it.

---

## Concept

SOCIAL CONTRACT is a simulation of political imagination. Students are assigned a civic profile — a real age, occupation, income, legal status, family situation, and set of constraints — and answer five civic dilemmas from that position. They then answer the same five dilemmas as themselves. The gap between the two sets of answers is read.

The instrument does not claim to show how structural position *actually* shapes civic reasoning. It shows how students *imagine* it does. That imagination — where it is generous, where it is thin, where the student's own assumptions bleed into the assigned role — is the primary data.

> A superb simulation of political imagination rather than a direct model of lived civic experience.

That distinction matters and is stated explicitly in the intro screen. The instrument is honest about what it measures.

---

## The engine

**Two-mode gap mechanic.** Role mode first, self mode second. The same five dilemmas, answered twice from different positions. The AI reads the pattern of differences across all five — not individual dilemmas, but the structural pattern of the student's political imagination.

This is a civic extension of the gap engine used in *SELF v SELFIE*, applied to positional rather than personal identity.

---

## The civic profiles

Twelve curated profiles covering the structural spectrum. Random assignment from the pool, ensuring diverse positions are represented across a class session.

| Profile | Key position |
|---|---|
| Mariam, 34 | Single parent, two jobs, no sick pay |
| Edward, 67 | Retired, state pension, NHS-dependent |
| Viktor, 28 | Gig courier, no employment rights |
| Amara, 22 | Asylum seeker, prohibited from working |
| Richard, 51 | CEO, £1.4M salary, lobbies against regulation |
| Priya, 19 | First-generation student, accumulating debt |
| James, 44 | Recently redundant, skills non-transferable |
| Sophia, 38 | Disabled, dependent on public services |
| David, 58 | Rural farmer, dependent on subsidy policy |
| Fatima, 16 | Climate activist, too young to vote |
| Chen, 45 | Permanent resident, 12 years' taxes, no vote |
| Eleanor, 72 | Retired teacher, community volunteer |

Each profile includes: name, descriptor, six field rows (employment, income, family, legal status, major constraint, major stake), and a closing note framing their relationship to the civic contract.

**Why curated rather than pure random:** pure random risks clustering — a class where nobody gets an economically marginal profile learns less. The curated pool guarantees the structural spectrum is always represented.

---

## The five dilemmas

All stated neutrally. All genuinely hard across different positions.

| # | Dilemma |
|---|---|
| 1 | Progressive income tax increase (3%) to fund public services |
| 2 | Mandatory civic service for all adults aged 18–65 |
| 3 | 60% reduction in all immigration categories |
| 4 | Replacing universal public services with means-tested benefits |
| 5 | Mandatory 25% effective corporation tax, closing all loopholes |

Each dilemma offers three stances: Support / Oppose / Qualify. Both a stance and a written justification (minimum 20 characters) are required before the student can proceed.

---

## The reading

After both rounds, the model reads the full record as an analysis of political imagination.

**What the model reads for:**

**Role inhabitation** — did the student actually inhabit the assigned profile, or did their own values bleed into the role answers? A student playing the asylum seeker who supports harsh immigration restriction is not demonstrating how asylum seekers reason — they are demonstrating the limits of their imagination or empathy. The model names this directly.

**Pattern of difference** — which dilemmas produced the largest gaps and what those gaps suggest about how the student models structural inequality.

**Surprising similarity** — when role and self answers are similar, the model examines whether this reflects genuine alignment, failure to inhabit the role, or the student's assumption that a particular civic position is universal rather than positional.

**[empty] and [minimal] answers** — what a student couldn't or wouldn't justify from a particular position is primary data.

**Output:** headline (4–8 words, names the central finding about the student's political imagination), reading (200–270 words), signature (one sentence grounded in at least two specific answers), three discussion questions derived from role inhabitation, surprising similarity, and the student's model of inequality.

---

## The honest framing

The instrument is explicit about its limits from the intro screen:

> *"The gap between the two sets of answers will be read — not as proof of how structural position shapes reasoning, but as evidence of how you imagine it does. That imagination is itself worth examining."*

This is not a retreat from the concept's ambition. It is the more precise and more interesting claim. What students imagine about civic inequality — where their models are generous, where they are thin, where their own position distorts their understanding of others' — is valuable political knowledge. The instrument measures that, and says so.

---

## Pedagogical notes

**The most revealing outcome** is often not the largest gap but the smallest — when a student playing Amara (the asylum seeker) still supports strict immigration restriction, or playing Richard (the CEO) still supports corporate tax reform. This suggests either genuine cross-positional conviction or failure to inhabit the role. Both are worth discussion.

**The role reminder banner** appears throughout role mode, displaying the assigned profile's name and descriptor. Students cannot forget who they are answering as.

**The transition screen** between role and self modes is deliberate — a pause before the student answers as themselves.

**The result is private by default.** Students choose what, if anything, leaves the room.

**Discussion entry points** (generic — the instrument generates three specific ones per student):
- "Which dilemma was hardest to answer as your assigned profile? Why?"
- "Where did your own opinions bleed into the role answers — and what does that tell you?"
- "Which position in the profile pool would be hardest for you to inhabit? Why that one?"
- "The reading identified a limit in your imagination. Do you agree — and if it's wrong, why might it be wrong?"

---

## Abitur Themenfeld relevance

| Themenfeld | Angle |
|---|---|
| The Individual & Society | Class, structural inequality, civic obligation, conformity and resistance |
| Politics, Culture & Society — UK | British civic contract; immigration; class and public services; institutional trust |
| Politics, Culture & Society — USA | American civic contract; taxation; immigration; the gap between civic ideals and lived experience |

SOCIAL CONTRACT is the instrument in this suite most directly relevant to the **Politics, Culture & Society** Themenfelder. It connects postcolonial critique (Amara, Chen) to civic theory (the contract) to class analysis (Richard vs. Mariam) in a single session.

---

## Suite relationship

SOCIAL CONTRACT is designed as the second instrument in a two-session sequence with **RPG4LIFE**:

1. **RPG4LIFE** — students examine their own identity build: which roles were assigned, which were chosen, what the hidden costs are.
2. **SOCIAL CONTRACT** — students inhabit someone else's build and discover that the rules of the civic game land differently depending on starting stats.

The contrast between the two sessions is where structural critique becomes legible: you understand your own position, then you try to inhabit another's, and the gap in your imagination tells you something about both.

---

## Technical architecture

Uses the same Cloudflare Worker proxy as the rest of the suite.

```javascript
const PROXY = "https://anthropic-proxy.justin-steinmetz.workers.dev";
```

One API call per session — the civic record reading at the end. See the *Who Are You, Really* README for full Worker deployment instructions.

### Deployment

Single HTML file. No dependencies, no build step. Rename `social-contract.html` to `index.html` and push to a GitHub Pages repository.

