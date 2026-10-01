# UCI 2227 — Module 524 lab tools

Forty-three self-contained HTML lab simulators for **Module 524: Critical Facilities Technician
Day-One Readiness Immersion**. Each one runs a data-center scenario, collects the learner's answers,
and exports a single PDF for upload to Canvas.

No build step. No dependencies. No network calls. Open a file in a browser and the lab starts.

---

## ⚠️ Read this before you push

**On the GitHub Free plan, GitHub Pages only serves from a _public_ repository.** Making the repo
private automatically unpublishes the site. Private Pages sites require an organization account on
GitHub Enterprise Cloud. So assume from the outset that **anything you commit here is world-readable
and search-engine indexable.**

Three consequences.

### 1. Never commit the facilitator builds

The thirteen `*_FT.html` files contain the **answer keys** in an instructor drawer. `SET_KEY.md` maps
every scenario letter to the fault it hides. Neither belongs in a public repo, and the `.gitignore`
in this folder blocks both. Distribute them through Canvas instructor files, a private repo, or
Drive — never here.

```
524-1-1_SafetyZones_FT.html      ← never commit
524-1-3_LiveDeadLive_FT.html     ← never commit
… all 13 _FT.html files
SET_KEY.md                       ← never commit
524_Facilitator_Guide.docx       ← never commit
```

### 2. The scenario logic is in the client, and always was

These are client-side simulators. The seeded fault, the alarm bands and the pass conditions are all
in the JavaScript, and always have been — a learner with the file on a USB stick could read them too.
Public hosting does not create that exposure, but it does make it trivially discoverable and puts it
in reach of a search engine.

If that matters for your graded gates, the mitigations are instructional rather than technical, and
you already have them: rotate sets between adjacent stations, keep the set register, and lean on the
verbal verification that 524.2.1, 524.3.3, 524.5.2 and 524.5.3 already build into their assessment.
A learner who has read the source still has to explain their trace out loud.

### 3. URLs are guessable

`524-1-3-A_LiveDeadLive.html` implies `-B`, `-C` and `-D`. A learner given one set can reach the
others by editing the address bar. This is the same exposure as point 2 and has the same answer —
the set letter is deliberately meaningless, and the register is what ties a submission to a key.

---

## What is in this folder

| | |
|---|---|
| **43** lab tool files | 16 labs × their scenario sets |
| **3.3 MB** total | comfortably inside the 1 GB Pages limit |
| **0** external requests | no CDN, no fonts, no analytics, no tracking |
| **216** questions | across the sixteen labs |

A **Lab** is the graded unit — one handout, one question set, one Canvas assignment, one rubric. A
**Lab tool** is one scenario variant of a Lab. The lettered files are *alternates, not sequential
parts*: a learner runs one and hands in one PDF.

| Lab | Title | Files | Sets | Questions |
|---|---|---|---|---|
| 524.1.1 | Safety Zone Mapping | `524-1-1-{A,B,C}_SafetyZones.html` | 3 | 16 |
| 524.1.2 | PPE Selection and Multi-Source Lockout | `524-1-2_PPELockout.html` | 1 | 18 |
| 524.1.3 | Live-Dead-Live Verification | `524-1-3-{A,B,C,D}_LiveDeadLive.html` | 4 | 16 |
| 524.1.4 | Stop-Work Roleplay and Escalation Log | `524-1-4_StopWork.html` | 1 | 14 |
| 524.2.1 | Power Path Tracing | `524-2-1-{A,B,C}_PathTrace.html` | 3 | 16 |
| 524.2.2 | Which Source Is Carrying the Load? | `524-2-2-{A,B}_SourceID.html` | 2 | 16 |
| 524.2.3 | Telemetry Simulation Audit | `524-2-3-{A,B,C,D,E}_LoadBank.html` | 5 | 11 |
| 524.3.1 | Map the Thermodynamic Loops | `524-3-1-{A,B,C}_LoopMap.html` | 3 | 13 |
| 524.3.2 | Thermal Envelope Audit | `524-3-2-{A,B,C}_ThermalAudit.html` | 3 | 11 |
| 524.3.3 | Chiller Loop Fault Diagnosis | `524-3-3-{A,B,C,D}_ChillerFault.html` | 4 | 17 |
| 524.4.1 | Classify the Document Library | `524-4-1-{A,B}_DocSort.html` | 2 | 16 |
| 524.4.2 | Execute a Rack PDU Replacement MOP | `524-4-2_MOPExec.html` | 1 | 13 |
| 524.4.3 | MOP Rollback Execution Gate | `524-4-3-{A,B,C}_MOPRollback.html` | 3 | 14 |
| 524.5.1 | Full Facility Round | `524-5-1-{A,B,C}_Round.html` | 3 | 8 |
| 524.5.2 | Twenty Alarms at Once | `524-5-2-{A,B}_AlarmFlood.html` | 2 | 10 |
| 524.5.3 | SBAR Turnover Verification Gate | `524-5-3-{A,B,C}_SBAR.html` | 3 | 7 |

**524.1.2 and 524.1.4 have no simulator.** Both labs are assessed on the floor by the instructor;
their tools carry the lab's packet (work order, one-line and lockout log; escalation matrix, incident
report and escalation log), the written record and photographs, and their submission PDF says so.

**Packets live inside the tools.** Every paper item a handout names — legend sheet and worksheet,
baseline sheet, RCA tree and fix ticket, Level of Risk matrix, the MOP field copy and tracking log, the
known-fault log, the shift log and SBAR template — is behind a **Packet** button in the tool (a
**Packet ↗** popup in 524.1.1 and 524.5.1). Each packet prints on its own, and any field a packet asks the
learner to fill is captured into the submission PDF.

---

## Deploying

This repository is
[`platformps/Module-524-Critical-Facilities-Technician-Day-One-Readiness`](https://github.com/platformps/Module-524-Critical-Facilities-Technician-Day-One-Readiness).

**Easiest — no tooling.** Open
[the upload page](https://github.com/platformps/Module-524-Critical-Facilities-Technician-Day-One-Readiness/upload/main)
and drag in everything from the `Lab Tools` folder. The facilitator builds live in a *different*
folder, so you cannot pick them up by accident.

**Or run `PUSH-TO-GITHUB.bat`** from the parent folder. It commits and pushes, checks for instructor
files before it does, and authenticates through a normal browser sign-in — no token to create.

```bash
git init && git checkout -b main
git add .
git commit -m "Module 524 lab tools"
git remote add origin https://github.com/platformps/Module-524-Critical-Facilities-Technician-Day-One-Readiness.git
git push -u origin main
```

Then **Settings → Pages → Source: Deploy from a branch → `main` / `(root)` → Save**.

Labs go live about a minute later:

```
https://platformps.github.io/Module-524-Critical-Facilities-Technician-Day-One-Readiness/524-1-1-A_SafetyZones.html
```

There is nothing to configure: no Jekyll front matter, no workflow file, no build.

Those URLs are long. If you are pasting them into Canvas by hand a lot, a shorter repository name —
or a custom domain under **Settings → Pages** — would pay for itself.

`.nojekyll` is included so Pages copies the files verbatim instead of running them through Jekyll.
Nothing here needs Jekyll and nothing here would survive it being clever.

### Limits you will not hit

GitHub Pages allows **1 GB per site**, a soft **100 GB/month** bandwidth limit and a soft **10 builds
per hour**. This folder is 3.3 MB and each learner loads a few hundred KB once. A 200-learner cohort
running the whole module moves well under a gigabyte a month.

---

## Wiring it into Canvas

**Link, do not embed.** Add each lab as an External URL in the Canvas module, opening in a new tab.
Iframing works — GitHub Pages sets no `X-Frame-Options` — but the labs assume a full viewport, they
are designed at 1280×720 and up, and the print path is cleaner from a real tab than from inside a
Canvas frame.

Sixteen Canvas assignments, one per Lab, each accepting **one PDF file upload**. Do not create
forty-three: no learner runs more than one set of a lab, so twenty-seven columns would sit
permanently empty for every student.

Hand each station a specific set URL and record which learner got which. The submission PDF names its
set on every page, so an instructor can always confirm which key to mark against.

---

## How a learner submits

1. Open the lab URL the instructor gives them. It opens straight into the scenario.
2. Work the simulator (and the **Packet**, where the handout sends you there), then press its own **Build submission sheet**.
3. Answer every question in the **Lab submission** panel underneath.
4. Enter name and cohort, press **Build submission PDF**, choose **Save as PDF**.
5. Upload that one file to the matching Canvas assignment.

The PDF carries the learner name, cohort, scenario set, the simulator's record and every question
with its response, plus any photograph attached. The paper handout is an instruction sheet and is
never handed in.

The browser suggests `Lastname_Firstname_524.x.y.pdf` as the filename automatically.

**If the print dialogue offers no PDF option**, the machine has a physical printer as its default —
change the destination to *Save as PDF* in the dialogue itself.

---

## Storage behavior, and why it matters more when hosted

Answers are kept in `localStorage` as the learner types, so a refresh or an accidental close does not
lose the work.

**Hosting changes the arithmetic.** Opened from a USB stick every file is its own context; served
from `<org>.github.io` **all forty-three labs share one origin and one ~5 MB budget**. Seventeen
image questions across the module at roughly 325 KB each is about 5.4 MB — a learner working through
the whole course on one browser profile would otherwise run out near the end.

The tools handle this themselves:

- Attached images are downscaled to 1600 px JPEG before storage. An 11.4 MB phone photo stores as
  about 325 KB.
- When room is needed, images belonging to **other** labs are evicted — already-exported labs first,
  then oldest. Those images are already inside the PDF that lab produced.
- **Typed answers are never evicted.** They are small, and they are the part a learner cannot
  reproduce.
- If an image is dropped from a lab that had not yet been exported, that lab says so on next open and
  asks for it again.
- If storage fails outright — private browsing, or storage switched off — a red banner appears telling
  the learner to build the PDF now rather than refresh.

Storage is per browser, per machine. **A learner who changes benches mid-lab starts with an empty
form.** If a bench has to change, have them build and save the PDF first.

---

## Browser support

Any current Chrome, Edge, Firefox or Safari. Chromium-based browsers give the best print output.

The labs are **desktop-first**: designed at 1280×720 and up, and they degrade rather than respond
below about 1024 px. Nothing becomes unreachable on a tablet, but layouts get cramped and some inner
tables need horizontal scrolling. A training-room laptop is the intended device.

JavaScript is required. There is no server, no account and no data leaves the machine — nothing is
transmitted anywhere, which is also why nothing is recoverable if a learner clears their browser
storage before exporting.

---

## Accessibility

The submission panel in every file meets **WCAG 2.1 AA**: every field is programmatically labeled,
headings are real headings, images carry alt text, the completeness check announces through a live
region, and focus is visible throughout.

**The simulators above it are not there yet.** Known gaps, in priority order:

- Simulator inputs in several families still use visual labels without programmatic association
  (the packet fields, the submission panel, and Round's inputs are all labeled).
- The eight canvas charts in LoadBank and ChillerFault have no text equivalent.

Closed on 3 September 2026: 524.5.3 (SBAR) can now be completed with a keyboard — the 26 log rows,
the sort headers, filter chips and the four confirmation ticks are focusable and operable with Enter
or Space — and 524.5.2's headers, chips and ticks likewise.

`DESIGN-REVIEW.md` in the parent folder carries the full findings and a prioritized fix list.

---

## Editing these files

Each file is one self-contained HTML document: the simulator, then a `<!-- LQ_SUBMISSION_MODULE -->`
marker, then the shared submission module.

**Do not hand-edit the questions.** The question list in each `<script id="lqData">` block is
generated together with the matching handout, and the two must stay in lockstep — the handout's
`→ Answer this as Q7 in the lab tool` pointers are numbered from the same source. Editing one alone
silently desynchronizes them. Regenerate both.

The module is identical across all 43 files. A fix belongs in the shared source and gets re-injected,
not patched in one file. **`7_Record/regen_lq.py` does both** — it rebuilds every `lqData` block from
the matching handout and re-injects the module — so the workflow after any edit is: change the handout
or the module source, run the script, re-test.

**The `window.lqRecord()` hook.** A simulator whose record lives inside a pane that gets repainted
defines `window.lqRecord = () => sheetHTML()` — a function that builds the sheet from state and returns
an HTML string (or `null`, optionally setting `window.lqRecordReason`). The module calls it first, so
the PDF carries the record whichever pane the learner is looking at; the `.result.show` harvest and
the auto-click of **Build submission sheet** remain as the fallback for the simulators that need neither.

See `docs/adr/` in the parent folder for why the submission model is shaped the way it is —
particularly `0002-print-to-pdf-not-a-bundled-library.md`, which explains why there is no PDF library
here and why adding one would break submissions inside Canvas.

---

## License and attribution

Per Scholas / UCI 2227 course material. Add your license terms before making the repository public —
an unlicensed public repo grants no reuse rights, which may or may not be what you intend.

Sources: [GitHub Pages limits](https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits) ·
[Creating a GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site) ·
[Setting repository visibility](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/setting-repository-visibility)

## v2.3 — readability rework (29 September 2026)

Learner feedback on the labs: the instructions were vague and the colors made the tools hard to read. Every tool now:

- opens on a **How to work this lab** card — numbered steps naming the exact panel and button for each action, what you should see after it, a "you are finished when" list, and tips. It collapses (click the heading) and stays collapsed in that browser until you open it again. It does not print.
- uses a **light, high-contrast page** (white panels, near-black text, AA-checked colors) with a 12 px type floor and 15 px body text. Where a tool shows a console, chart or diagram, that part keeps its dark "screen" look on purpose.

The change is applied by `build/readability_patch.py` (with the guide text in `guides_524.py`), so it can be re-run over a regenerated set of tools. `build/test_readability.py` renders every tool headless and checks JS errors, the guide card, the type floor and contrast.

## v2.4 — goals and scenario at the top (30 September 2026)

Review feedback on the labs: keep the deeper electrical and mechanical instruction and the lab walkthroughs, and move each lab's goals and scenario to the top in bold or contrasting text. Every tool now:

- opens on a **Goals + Scenario band** directly under the toolbar and above the *How to work this lab* card — bold white text on navy, always visible, not collapsible. It does not print, so the submission PDF is unchanged.
- takes that wording from its own handout: the handout's *Learning Objectives* are the goals, and the first paragraph under its scenario heading is the scenario. The handout stays the single source — edit the handout, re-run the patch.

Nothing else in any tool changed. Remove the block between the `GS_BRIEF` markers and each file is byte-identical to its v2.3 version: every simulator panel, packet, question and guide step is where it was.

The sixteen lab handouts carry the matching change: *Learning Objectives* and a new *Scenario* heading lead the document, in bold on a shaded block between two rules; the Introduction and the numbered steps follow unchanged under *Introduction*, *Equipment/Requirements* and *Instructions*.

The change is applied by `build/goals_scenario_patch.py <handouts folder> <tools folder>`. It is re-runnable (a second run changes nothing) and works on both modules. Run it last: after `regen_lq.py` and after the readability patch, because it anchors on the guide card. `build/test_goals_scenario.py` renders every tool headless and checks the band's position, weight, contrast and wording, that nothing outside the band changed, and that no handout text was lost.

## v2.5 — a wrong answer says so (30 September 2026)

Learner request: when an answer is wrong, make it obvious — a sound, or the word in big letters. Both are now in the tools that check an answer.

In this module that is **GLAB 524.2.1 Power Path Tracing** (`524-2-1-A / B / C`), the one lab whose tool refuses a wrong move. Clicking a device that is not a source, not connected to the current point, or already on the path now shows **WRONG** in big letters with the reason under it ("Why: That is not connected to your current point. You are at …"), and a short buzzer sounds. The box stays up until the next click or key, so there is time to read it. *Open the legend first* is a prompt, not a wrong answer, and stays as it was.

- **Sound on / Sound off** is the switch in the bottom-left corner of the page. The choice is remembered in that browser.
- The other forty tools are unchanged, byte for byte. They record judgment calls for the instructor to assess and never tell a learner right or wrong, so there is nothing for the signal to attach to — and no answer key was added to any learner file.
- The signal does not print; the submission PDF is unchanged.

Applied by `build/wrong_signal_patch.py <tools folder>` (re-runnable; run it after any regeneration). `build/test_wrong_signal.py` drives a wrong move in each tool and checks the box, the reason, the buzzer, the Sound switch and that nothing else changed.

## v2.7 — short instructions (1 October 2026)

Learner feedback: the goals and scenario are easy to spot, but the instructions under them were wordy. The long "How to work this lab" card is now a short **Steps for this lab** card, about a quarter of the reading (half in GLAB 524.1.1, which also teaches the routine).

- **One line per step.** Each step says what to do and where. Press **More** on a step for the full explanation of that step, including what you should see when it works.
- **The routine is taught once.** Saving your records, answering the questions and building the PDF are the same in every lab, so GLAB 524.1.1 spells that routine out under **Start here**, with one worked example. Every other lab has one line for it at the foot of the card.
- **Nothing was thrown away.** **Full instructions** at the foot of the card opens the complete earlier card: every step in full, what you hand in, the finish checklist and the tips.
- A collapsed card stays collapsed in that lab. The card does not print: the submission PDF is unchanged.
- In GLAB 524.1.2 and 524.1.4 the "How this lab is submitted" box said the same things again, so it now sits under **Full instructions** too.
- While the steps were being shortened, every one was walked against the live tool, and the earlier wording was corrected where it did not match. Examples: in 524.4.2 and 524.4.3 the button is **Act**, not "Do it"; in 524.5.1 readings are typed on the **Route** tab and **Capture** belongs to the **Thermal** tab; in 524.5.3 **Cite** is on the **Briefing mode** tab; in 524.1.1 noise zones are drawn by dragging.
- The steps now point at the packet worksheets and extra fields that **Build submission sheet** asks for (524.2.1, 524.2.2, 524.2.3, 524.3.3, 524.5.1, 524.5.2).

The change is applied by `build/short_guide_patch.py <tools folder>` (re-runnable, in any order with the other patches; run it after any regeneration). `build/test_short_guide.py <tools before> <tools after>` checks it. To reword a step, edit the `SHORT` table at the top of the patch and run it again.
