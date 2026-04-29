# `_data/` — Field Reference

This folder contains the two main data files that drive most of the site's
dynamic content. Each file starts with a comment block summarising its
schema — this README collects both in one place for quick reference.

---

## `people.yml`

Controls every card on the [People](https://hiro-group.ronc.one/people) page.
Entries are rendered in the order they appear within each role group.

### Required fields

| Field  | Description |
|--------|-------------|
| `name` | Full display name, e.g. `"Dr. Alice Smith"` |
| `role` | Section the person appears in — see role table below |

### Role values (in display order)

| Role | Section |
|------|---------|
| `faculty` | Principal Investigator(s) |
| `labmanager` | Lab Manager |
| `postdoc` | Post-doctoral Researchers |
| `phd` | PhD Students |
| `grad` | MS / Graduate Students |
| `undergrad` | Undergraduate Students |
| `highschool` | High School Students |
| `collaborator` | Visiting / External Collaborators |
| `alumni-spotlight` | Featured alumni (spotlight card, needs extra fields) |
| `alumni` | All other alumni |

### Optional fields

| Field | Description |
|-------|-------------|
| `pic` | Photo filename in `/img/people/`, e.g. `alice.jpg` |
| `url` | Personal / lab website URL |
| `email` | CU Boulder email address |
| `phone` | Phone number string |
| `office` | Office room, e.g. `ECES 124` |
| `linkedin` | LinkedIn **slug only** (not the full URL), e.g. `alice-smith` |
| `page` | Slug for an internal CV/profile page, e.g. `anuj` |
| `subteam` | Research group: `embodied-intelligence` or `social-intelligence` |
| `graduated` | Degree + year string, e.g. `"HIRO Ph.D. [2020–2025]"` |
| `nowat` | Current position after leaving the lab |

### Example

```yaml
- name: Alice Smith
  role: phd
  subteam: embodied-intelligence
  url: https://alicesmith.github.io
  email: alice.smith@colorado.edu
  pic: alice.jpg
  page: alice          # enables an internal profile at /people/alice

- name: Bob Jones
  role: alumni-spotlight
  subteam: social-intelligence
  url: https://bobjones.com
  graduated: "HIRO Ph.D. [2018-2023]"
  nowat: Assistant Professor at MIT
  pic: bob.jpg
```

---

## `publications.yml`

Powers the [Publications](https://hiro-group.ronc.one/publications) page and
all per-person / per-subteam publication lists.

### Required fields

| Field | Description |
|-------|-------------|
| `title` | Full title (quote if it contains colons) |
| `authors` | Author list string; wrap a name in `<b>…</b>` to bold it |
| `year` | Publication year (integer) |
| `venue` | Full venue / journal name |
| `subteams` | List of tags — controls filtering, badges, and rendering |

### Optional content fields

| Field | Description |
|-------|-------------|
| `where` | Location and dates of the venue |
| `description` | Free-text note below the authors (HTML allowed) |
| `award` | Award text shown with a 🏆 icon |

### Optional button fields

| Field | Button shown | Notes |
|-------|-------------|-------|
| `pdf` | **PDF** + **BIB** | Filename without extension in `/papers/`, e.g. `2025_Smith_ICRA` |
| `code` | **Code** | Full URL to a code repository |
| `url` | **URL** | Full URL to an external page (project page, DOI, etc.) |
| `site` | *(reserved)* | Internal Jekyll page slug — not yet rendered in the card |

### Optional hosting field

| Field | Description |
|-------|-------------|
| `host` | Base URL override for PDF/BIB links. Defaults to `https://hiro-group.ronc.one` |

### Subteams tag reference

**Publication type** (determines badge colour — pick exactly one):

`conference` · `journal` · `workshop` · `thesis` · `book`

**Research area** (determines field badge — pick at most one):

`embodied intelligence` · `social intelligence`

**Person tags** (for per-person CV filtering):

`anuj` · `ava` · `caleb` · `carson` · `chi-hui` · `clare` · `gilberto` ·
`guohui` · `jake` · `joewie` · `kayleigh` · `nataliya` · `naren` ·
`srikrishna` · `stephane` · `yi-shiuan` · *(add new ones as needed)*

**Topic tags** *(currently not used for rendering, kept for legacy filtering)*:

`algorithmic hri and human-ai teaming` · `control and artificial skin` ·
`learning and modeling` · `physical hri`

### Example

```yaml
- title: "My Awesome Paper"
  authors: Alice Smith, Bob Jones, Alessandro Roncone
  year: 2025
  venue: "IEEE International Conference on Robotics and Automation [ICRA]"
  where: Atlanta, Georgia, USA, May 19-23
  award: Best Paper Award!!
  description: Extended abstract
  pdf: "2025_Smith_ICRA_awesome"
  code: "https://github.com/hiro-group/awesome"
  url: "https://hiro-group.ronc.one/awesome/"
  host: "https://alessandro.ronc.one"   # omit to default to hiro-group.ronc.one
  subteams: [learning and modeling, alice, conference, embodied intelligence]
```
