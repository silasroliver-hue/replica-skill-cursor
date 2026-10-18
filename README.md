# The Replica skill

Eleven Cursor skills that clone any app. Free, MIT, no signup, no API key,
nothing to connect.

One reverse-engineers the app you want to clone. One rebuilds it. One tests it
for bugs. And one is the Entrepreneur: it reads what the app's users hate and
fixes it in yours, so you have an app you can sell.

In between, the others plan the stack and the database, rebuild the design
system, wire up auth and payments, score your clone against the original, give
it a name and a brand of its own, write the landing page and the store
listing, and put it live on your domain.

**It rebuilds what an app does, never what it owns.** Features and flows,
clean-room style. Not its code, its logo, its copy or its content. The
fine print is at the bottom, and the skills enforce it.

Ported for Cursor from the Claude pack
[Jakeschincariol/replica-skill](https://github.com/Jakeschincariol/replica-skill).

## Install in Cursor

This repo already ships the pack under `.cursor/skills/`. Open the project in
Cursor and ask the Agent to run a skill by name, for example:

```
Run replica-recon on https://example.com
```

or:

```
clone this app: https://example.com
```

The Agent matches skills from each `SKILL.md` description.

### Copy into another project

```bash
cp -r .cursor/skills/replica-* /path/to/your-project/.cursor/skills/
```

Create `.cursor/skills/` in the target project first if it does not exist.

### Global Cursor skills (optional)

If your Cursor setup loads personal skills from a global folder, copy the same
`replica-*` directories there so every project can use them.

## The eleven

| skill | what it does |
| --- | --- |
| `replica-recon` | Reverse-engineers any app: screens, flows, components, data model. From public pages, screenshots, store listings and your own account. |
| `replica-architect` | Plans the stack, database schema and API for your clone. |
| `replica-design` | Rebuilds the design system: colours, type, spacing, components. As tokens, with your own assets. |
| `replica-build` | Rebuilds the app screen by screen from the recon map. |
| `replica-backend` | Auth, database, payments and integrations. |
| `replica-test` | Clicks through every flow and tests it for bugs. |
| `replica-diff` | Compares your clone against the original. A parity score and what is missing. |
| `replica-entrepreneur` | Reads what the app's users hate in real reviews and turns it into fixes and a positioning angle. |
| `replica-brand` | Names and rebrands your version so it is yours. |
| `replica-launch` | Landing page, pricing and App Store listing. |
| `replica-deploy` | Ships it live on your own domain. |

## How to use it

Run them in order. Each one reads what the last one wrote, in a `replica/`
folder in your project.

```
recon -> architect -> design -> build -> backend -> test -> diff -> entrepreneur -> brand -> launch -> deploy
```

You can also run any one on its own. `replica-entrepreneur` on an app you
are only thinking about cloning is a good way to find out if you should.

## The tools

Six of them, all standard-library Python. Nothing to pip install. Python 3.8+.

```bash
python3 .cursor/skills/replica-diff/imgdiff.py original.png clone.png --out diff.png
python3 .cursor/skills/replica-diff/parity.py replica/features.csv
python3 .cursor/skills/replica-entrepreneur/reviews.py replica/reviews.csv
python3 .cursor/skills/replica-design/contrast.py replica/design/tokens.json
python3 .cursor/skills/replica-brand/sweep.py . --avoid "Original App"
python3 .cursor/skills/replica-launch/listing.py replica/launch/listing.json
```

```bash
python3 -m unittest discover -s tests -v
```

## Fine print

**It rebuilds functionality and UX patterns, clean-room style.** It studies
what the app does and how people move through it, then writes everything
fresh. It never copies the target's source code, proprietary assets, logos,
trademarks, copy or private APIs.

**It only reads what you are allowed to read.** Public pages and your own
account. It never scrapes behind a login or against a site's terms, never
logs into anyone else's account, and never gets past a paywall. If your
account's terms forbid using it to build a competitor, it says so and sticks
to public sources.

**It always rebrands before launch.** New name, new palette, new logo, new
words. `replica-deploy` will not ship until the sweep is clean.

**"Clone any app" means the features and the flow.** Not the content, the
network or the licences an app owns.

**The Entrepreneur never makes things up.** No invented reviews, quotes or
numbers. Every claim has a link, and the sample size is stated.

**Check before you sell.** Run the trademark checks `replica-brand` lists,
read the terms of anything you used, and talk to a lawyer before launch if
there is money on the line. This is not legal advice.

## Files

```
.cursor/skills/replica-recon/         SKILL.md, recon-map.md, features.csv
.cursor/skills/replica-architect/     SKILL.md, architecture.md
.cursor/skills/replica-design/        SKILL.md, tokens.json, contrast.py
.cursor/skills/replica-build/         SKILL.md
.cursor/skills/replica-backend/       SKILL.md
.cursor/skills/replica-test/          SKILL.md, test-plan.md, bug-report.md, e2e.example.spec.ts
.cursor/skills/replica-diff/          SKILL.md, imgdiff.py, parity.py
.cursor/skills/replica-entrepreneur/  SKILL.md, reviews.py, themes.json
.cursor/skills/replica-brand/         SKILL.md, sweep.py
.cursor/skills/replica-launch/        SKILL.md, listing.py, listing.example.json
.cursor/skills/replica-deploy/        SKILL.md, preflight.md
tests/                                tests for every tool
```

Your own files live in `replica/` in the project you are cloning into. The
skills read each other's outputs there.

## Credit

Original pack by Jake Schincariol, [opusjake.ai](https://opusjake.ai).
Upstream: [Jakeschincariol/replica-skill](https://github.com/Jakeschincariol/replica-skill).
This repo adapts the same skills for Cursor project skills under `.cursor/skills/`.

## License

MIT. Take it, change it, ship it.
