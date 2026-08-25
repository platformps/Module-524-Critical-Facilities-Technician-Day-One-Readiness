# UCI 2227 — Module 524 lab tools

Forty-three self-contained HTML lab simulators for **Module 524: Critical Facilities Technician
Day-One Readiness Immersion**. Each one runs a data-centre scenario, collects the learner's answers,
and exports a single PDF for upload to Canvas.

No build step. No dependencies. No network calls. Open a file in a browser and the lab starts.

---

## ⚠️ Read this before you push

**On the GitHub Free plan, GitHub Pages only serves from a _public_ repository.** Making the repo
private automatically unpublishes the site. Private Pages sites require an organisation account on
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
| 524.2.3 | Generator Load-Bank Telemetry Audit | `524-2-3-{A,B,C,D,E}_LoadBank.html` | 5 | 11 |
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
their tools capture the written record and photographs only, and their submission PDF says so.

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
2. Work the simulator, then press its own **Build submission sheet**.
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

## Storage behaviour, and why it matters more when hosted

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

The submission panel in every file meets **WCAG 2.1 AA**: every field is programmatically labelled,
headings are real headings, images carry alt text, the completeness check announces through a live
region, and focus is visible throughout.

**The simulators above it are not there yet.** Known gaps, in priority order:

- **524.5.3 (SBAR) cannot currently be completed with a keyboard.** Its builder unlocks only after all
  26 shift-log entries are opened, and those rows are not keyboard-reachable. Learners who need
  keyboard access must be given an alternative route through this lab.
- Simulator inputs use visual labels without programmatic association.
- The eight canvas charts in LoadBank and ChillerFault have no text equivalent.

`DESIGN-REVIEW.md` in the parent folder carries the full findings and a prioritised fix list.

---

## Editing these files

Each file is one self-contained HTML document: the simulator, then a `<!-- LQ_SUBMISSION_MODULE -->`
marker, then the shared submission module.

**Do not hand-edit the questions.** The question list in each `<script id="lqData">` block is
generated together with the matching handout, and the two must stay in lockstep — the handout's
`→ Answer this as Q7 in the lab tool` pointers are numbered from the same source. Editing one alone
silently desynchronises them. Regenerate both.

The module is identical across all 43 files. A fix belongs in the shared source and gets re-injected,
not patched in one file.

See `docs/adr/` in the parent folder for why the submission model is shaped the way it is —
particularly `0002-print-to-pdf-not-a-bundled-library.md`, which explains why there is no PDF library
here and why adding one would break submissions inside Canvas.

---

## Licence and attribution

Per Scholas / UCI 2227 course material. 
Sources: [GitHub Pages limits](https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits) ·
[Creating a GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site) ·
[Setting repository visibility](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/setting-repository-visibility)
