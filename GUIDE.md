# Website Editing Guide

A step-by-step guide for adding and editing content on the [Information Visions Lab website](https://infovisions.github.io/). This guide assumes no prior experience with GitHub, code, or web development.

---

## Table of Contents

1. [How This Website Works](#1-how-this-website-works)
2. [How to Edit Files on GitHub](#2-how-to-edit-files-on-github)
3. [Editing and Testing Locally](#3-editing-and-testing-locally)
4. [Site File Structure](#4-site-file-structure)
5. [YAML and Markdown Basics](#5-yaml-and-markdown-basics)
6. [Lab Members](#6-lab-members)
7. [Projects](#7-projects)
8. [Publications](#8-publications)
9. [News Items](#9-news-items)
10. [External Collaborators](#10-external-collaborators)
11. [Images](#11-images)
12. [Quick Reference](#12-quick-reference)

---

## 1. How This Website Works

The lab website is built from plain text files stored in this GitHub repository. When you edit a file and save your changes, GitHub automatically rebuilds the website and publishes it. You don't need to install anything on your computer — everything can be done through GitHub's website.

Here's the basic flow:

```
Edit a file on GitHub  →  Click "Commit changes"  →  GitHub rebuilds the site (1-2 min)  →  Changes appear on the live site
```

The website uses a tool called **Jekyll** to transform your text files into web pages. You write content in simple formats (YAML for structured data, Markdown for text), and Jekyll handles the rest.

> **Important:** After committing a change, it takes 1–2 minutes for the site to rebuild. If you don't see your changes right away, wait a moment and refresh.

---

## 2. How to Edit Files on GitHub

### Editing an existing file

1. Go to [the repository on GitHub](https://github.com/infovisions/infovisions.github.io)
2. Navigate to the file you want to edit by clicking through the folders (for example, `_members/` → `evan-peck.md`)
3. Click the **pencil icon** (edit button) in the top-right corner of the file view
4. Make your changes in the editor
5. Scroll down to the **"Commit changes"** section
6. Write a brief message describing what you changed (e.g., "Updated my bio" or "Added new project")
7. Make sure **"Commit directly to the `main` branch"** is selected
8. Click the green **"Commit changes"** button

### Creating a new file

1. Navigate to the folder where the file should go (e.g., `_members/`)
2. Click the **"Add file"** button → **"Create new file"**
3. Type the filename in the name box at the top (e.g., `jane-doe.md`)
4. Add your content in the editor
5. Commit using the same process described above

### Uploading images

1. Navigate to the correct images folder (e.g., `images/members/`)
2. Click **"Add file"** → **"Upload files"**
3. Drag and drop your image file or click to browse
4. Commit the upload

---

## 3. Editing and Testing Locally

If you'd rather work on the website from your own computer (instead of editing directly on GitHub), you can run a local copy of the site. This lets you preview your changes instantly before pushing them to GitHub. This section walks through the full setup.

### One-time setup

#### 1. Install prerequisites

You need three things installed on your computer: **Git**, **Ruby**, and **Bundler**.

**macOS:**

Ruby comes pre-installed on macOS, but the system version is often outdated. The recommended approach is to use [Homebrew](https://brew.sh/) to install a current version:

```bash
# Install Homebrew (if you don't already have it)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Ruby and Git
brew install ruby git
```

After installing Ruby via Homebrew, follow the instructions Homebrew prints to add Ruby to your PATH. Then install Bundler:

```bash
gem install bundler
```

**Windows:**

1. Install [Git for Windows](https://gitforwindows.org/)
2. Install Ruby using [RubyInstaller](https://rubyinstaller.org/) — choose the version **with DevKit**
3. After installation, open a new terminal and run: `gem install bundler`

**Linux (Ubuntu/Debian):**

```bash
sudo apt update
sudo apt install ruby-full build-essential git
gem install bundler
```

#### 2. Clone the repository

Open a terminal and navigate to where you want the project folder, then run:

```bash
git clone https://github.com/infovisions/infovisions.github.io.git
cd infovisions.github.io
```

This downloads the entire website to your computer.

#### 3. Install dependencies

From inside the project folder, run:

```bash
bundle install
```

This installs Jekyll and all the plugins the site needs. It may take a minute or two the first time.

### Running the site locally

Once setup is done, you only need one command to start the local preview server:

```bash
bundle exec jekyll serve --livereload
```

After a few seconds, you'll see output like:

```
Server address: http://127.0.0.1:4000
```

Open that URL in your browser. You'll see the site running locally on your computer. When you edit and save a file, the site automatically rebuilds and your browser refreshes.

Press **Ctrl+C** in the terminal to stop the server when you're done.

### The local workflow

Here's the typical workflow when editing locally:

```
1. Pull latest changes     →  git pull
2. Start the local server  →  bundle exec jekyll serve --livereload
3. Edit files in your editor (VS Code, etc.)
4. Preview in browser at http://127.0.0.1:4000
5. Repeat steps 3-4 until happy
6. Stage your changes      →  git add -A
7. Commit                  →  git commit -m "Describe what you changed"
8. Push to GitHub          →  git push
```

After pushing, GitHub Actions automatically rebuilds and publishes the live site (takes 1–2 minutes).

### Essential Git commands

| Command | What it does |
|---------|-------------|
| `git pull` | Downloads the latest changes from GitHub to your computer |
| `git status` | Shows which files you've changed |
| `git add -A` | Stages all your changes for committing |
| `git add filename` | Stages a specific file |
| `git commit -m "message"` | Saves your changes with a description |
| `git push` | Uploads your committed changes to GitHub |

### Troubleshooting

**"Command not found: bundle"** — Ruby or Bundler isn't installed or isn't on your PATH. Re-check the installation steps above.

**"Could not find gem"** — Run `bundle install` again from the project folder.

**Build errors in the terminal** — Read the error message carefully. The most common cause is a YAML syntax error in a file you recently edited. The error usually names the file and line number.

**Port already in use** — If you get an error that port 4000 is busy, either stop the other server process or use a different port:

```bash
bundle exec jekyll serve --livereload --port 4001
```

---

## 4. Site File Structure

Here's where everything lives in the repository:

```
infovisions.github.io/
├── _members/                  ← Lab member profiles
│   ├── evan-peck.md
│   ├── alice-goldfarb.md
│   └── ...
├── _projects/                 ← Research projects
│   ├── eco-vis.md
│   ├── career-values.md
│   └── ...
├── _collaborators/            ← External collaborators (not lab members)
│   ├── darakhshan-mir.md
│   └── ...
├── _data/                     ← Structured data files
│   ├── news.yaml              ← Homepage news items
│   ├── publications.yaml      ← Lab publications
│   └── types.yaml             ← Role definitions (don't edit)
├── images/                    ← All images
│   ├── members/               ← Member photos
│   ├── projects/              ← Project images (one subfolder per project)
│   ├── collaborators/         ← Collaborator photos
│   └── funding/               ← Funder logos
├── about/                     ← About page
├── projects/                  ← Projects listing page
├── team/                      ← Team listing page
├── resources/                 ← Resources page
└── index.md                   ← Homepage
```

**The folders you'll most commonly edit are `_members/`, `_projects/`, `_collaborators/`, `_data/`, and `images/`.**

---

## 5. YAML and Markdown Basics

Every content file on the website uses two formats: **YAML** for structured settings and **Markdown** for free-form text.

### YAML (the settings block)

At the top of every `.md` file, you'll see a block between two lines of three dashes (`---`). This is called **frontmatter** and it contains the structured data about that page — things like the person's name, their role, or a project's title.

```yaml
---
name: Jane Doe
role: phd
image: images/members/janed-photo.jpg
---
```

**Key YAML rules:**

| Rule | Right | Wrong |
|------|-------|-------|
| Use spaces, never tabs | `  name: Jane` (2 spaces) | `	name: Jane` (tab) |
| Put a space after the colon | `name: Jane` | `name:Jane` |
| Wrap text with special characters in quotes | `title: "AI & Ethics"` | `title: AI & Ethics` |
| Lists use `- ` (dash + space) on each line | See examples below | |

**YAML lists** (used for things like project leads or authors):

```yaml
# A list of items
lead:
  - frida-mudsam
  - alice-goldfarb
```

**YAML objects** (used for things like funding with multiple properties):

```yaml
# An object with named properties
funding:
  - name: "Mozilla Foundation"
    url: "https://foundation.mozilla.org"
    image: "images/funding/moz-foundation.svg"
```

### Markdown (the content area)

Everything **below** the second `---` line is your free-form content, written in Markdown. Here are the basics:

```markdown
## This is a Heading

Regular paragraph text. You can make text **bold** or *italic*.

Here's a [link to Google](https://google.com).

Here's a bulleted list:
- First item
- Second item
- Third item

Here's an image:
![Description of image](/images/projects/my-project/diagram.png)
```

**Common Markdown reference:**

| What you want | What you type | What it looks like |
|---------------|---------------|--------------------|
| Bold text | `**bold**` | **bold** |
| Italic text | `*italic*` | *italic* |
| Link | `[text](https://url.com)` | [text](https://url.com) |
| Image | `![alt text](/images/path.png)` | (displays the image) |
| Heading | `## Heading` | A section heading |
| Bulleted list | `- Item` | A bullet point |

---

## 6. Lab Members

### Where to edit

Each lab member has their own file in the **`_members/`** folder. The filename determines the URL — `jane-doe.md` becomes `infovisions.github.io/members/jane-doe/`.

### Member photo

Upload your photo to **`images/members/`**. Use the naming convention `firstnamelastinitial-photo.jpg` (e.g., `janed-photo.jpg`). Square or near-square photos work best since they are displayed as circles.

### Frontmatter fields

| Field | Required? | Description | Example |
|-------|-----------|-------------|---------|
| `name` | **Yes** | Your full name | `Jane Doe` |
| `image` | **Yes** | Path to your photo | `images/members/janed-photo.jpg` |
| `role` | **Yes** | Your role in the lab (see table below) | `phd` |
| `affiliation` | No | Your university/institution | `University of Colorado` |
| `description` | No | Custom title (overrides the default for your role) | `PI, Faculty` |
| `aliases` | No | Alternate names (used for citation matching) | See example below |
| `links` | No | Your web/social links (see table below) | See example below |

### Available roles

| Value | Displays as | Icon |
|-------|------------|------|
| `pi` | Principal Investigator | Microscope |
| `phd` | PhD Student | Graduation cap |
| `masters` | Master's Student | Graduation cap |
| `bam` | Bachelor's & Master's Student | Graduation cap |
| `undergrad` | Undergraduate Student | User-graduate |
| `affiliate` | Affiliate | User-tie |

### Available link types

| Value | What it links to |
|-------|-----------------|
| `home-page` | Your personal website (full URL) |
| `email` | Your email address |
| `github` | Your GitHub username (e.g., `jdoe` becomes `github.com/jdoe`) |
| `linkedin` | Your LinkedIn slug (e.g., `janedoe` becomes `linkedin.com/in/janedoe`) |
| `bluesky` | Your Bluesky handle |
| `google-scholar` | Your Google Scholar ID |
| `orcid` | Your ORCID ID (e.g., `0000-0001-2345-6789`) |
| `twitter` | Your Twitter/X handle |

### Complete example

Here is a full member file (`_members/jane-doe.md`):

```yaml
---
name: Jane Doe
image: images/members/janed-photo.jpg
role: phd
affiliation: University of Colorado
aliases:
  - Jane A. Doe
  - J. Doe
links:
  home-page: https://janedoe.com
  email: jane.doe@colorado.edu
  github: janedoe
  linkedin: janedoe
  bluesky: janedoe.bsky.social
---

Jane is a PhD student in Information Science and a member of the Information Visions Lab advised by [Evan Peck](https://infovisions.github.io/members/evan-peck/).

Before joining CU Boulder, Jane worked as a data journalist at the New York Times. Her research focuses on how people interpret uncertainty in data visualizations.
```

**What each part does:**
- The YAML block (between `---` lines) controls the structured sidebar: photo, name, role icon, links
- The Markdown body (after the second `---`) becomes the main content of your profile page
- `aliases` help match your name to publications that may use different name forms

---

## 7. Projects

### Where to edit

Each project has its own file in the **`_projects/`** folder. The filename is called the **slug** — it determines the URL and is used to link publications to the project.

For example, `eco-vis.md` creates the page at `infovisions.github.io/projects/eco-vis/` and publications use `eco-vis` in their `projects` field to link to it.

### Project images

Create a subfolder for your project in **`images/projects/`**. For a project file named `my-project.md`, create `images/projects/my-project/` and put your images there.

### Frontmatter fields

| Field | Required? | Type | Description |
|-------|-----------|------|-------------|
| `title` | **Yes** | text | Full project title |
| `subtitle` | No | text | Short tagline displayed below the title |
| `status` | **Yes** | `active` or `completed` | Controls which section the project appears in on the Projects page |
| `published` | No | `true` or `false` | Set to `false` to hide a project entirely (draft mode). Leave out or set `true` to show it. |
| `image` | No | file path | Card thumbnail image. If omitted, a default dark background is used. |
| `date_start` | No | year | When the project began (e.g., `2025`) |
| `date_end` | No | year | When the project ended. If omitted, "Present" is displayed. |
| `short_description` | **Yes** | text | Brief summary shown on the project **card** on the Projects listing page. Keep it to 1–2 sentences. |
| `lead` | No | list of slugs | Team members leading this project (filenames without `.md`) |
| `pi` | No | list of slugs | Principal investigators (filenames without `.md`) |
| `collaborators` | No | list of slugs | External collaborators (from `_collaborators/`) |
| `funding` | No | list | Funders — can be simple text strings or objects with `name`, `url`, and `image` |
| `resources` | No | list of objects | Links to papers, code, demos, etc. Each has `label` and `url`. |
| `news` | No | list of strings | Project-specific updates (Markdown supported) |

### Connecting people to projects

The `lead`, `pi`, and `collaborators` fields use **slugs** — the filename of a person's file without the `.md` extension.

For example, if the member file is `_members/frida-mudsam.md`, the slug is `frida-mudsam`. If the collaborator file is `_collaborators/darakhshan-mir.md`, the slug is `darakhshan-mir`.

```yaml
lead:
  - frida-mudsam
pi:
  - evan-peck
  - darakhshan-mir     # This person is in _collaborators/, and that's fine
```

These people will appear as small portrait thumbnails in the project sidebar AND their small avatar photos will appear at the bottom of the project card on the Projects page.

### Funding formats

You can list funders in two ways:

**Simple format** — just a text string:

```yaml
funding:
  - "National Science Foundation"
```

**Rich format** — with a logo image and/or link:

```yaml
funding:
  - name: "Mozilla Foundation"
    url: "https://foundation.mozilla.org"
    image: "images/funding/moz-foundation.svg"
```

You can mix both formats in the same list.

### Resources

Use resources to link to papers, code repositories, project websites, or demos:

```yaml
resources:
  - label: "Paper PDF"
    url: "https://example.com/paper.pdf"
  - label: "GitHub Repository"
    url: "https://github.com/infovisions/my-project"
  - label: "Live Demo"
    url: "https://my-demo-site.com"
```

### Complete example

Here is a full project file (`_projects/eco-vis.md`):

```yaml
---
title: "Ecological Model of Visualization"
subtitle: "Capturing the influence of context"
status: active
published: true
image: images/projects/eco-vis/eco-vis-literacy.png
date_start: 2026
lead:
  - frida-mudsam
pi:
  - evan-peck
resources:
  - label: "Workshop Paper"
    url: "https://example.com/paper.pdf"
funding:
  - name: "Mozilla Foundation"
    url: "https://foundation.mozilla.org"
    image: "images/funding/moz-foundation.svg"
news:
  - "**March 2026** — Paper accepted to [CHI 2026 Workshop on Data Literacy](https://example.com)"
short_description: "How do context, culture, and lived experience shape the way people read charts? We apply an ecological framework to visualization literacy to move beyond individual decoding skills."
---

Visualization interpretation does not just depend on the chart itself, but layers
of context surrounding it — from personal experience to rhetorical framing to
social context.

We translate Bronfenbrenner's Ecological Systems Theory to information
visualization to create a framework that both synthesizes prior research and
connects with adjacent disciplines like media studies and journalism.

- **Core layer (Visual Encoding):** What patterns can be read from the encodings?
- **Microsystem layer:** How do personal experiences shape interpretation?
- **Exosystem layer:** How is this visualization framed or contextualized?
- **Macrosystem layer:** What cultural assumptions does this visualization rely on?
- **Chronosystem layer:** How do time and historical context shape interpretation?

![A diagram comparing the original EST model with our applied model for visualization](/images/projects/eco-vis/ecological-model-vis.png)
```

**What each part does:**
- `status: active` — this project appears under "What are we working on?" on the Projects page
- `short_description` — the text shown on the small card on the Projects page (not the full detail page)
- The Markdown body — the full description shown on the project's own detail page
- `lead` and `pi` — these people appear in the sidebar of the project detail page and as tiny photos on the project card
- `image` — the thumbnail shown on the project card
- `news` — project-specific updates shown at the bottom of the detail page

### Hiding a draft project

If you're working on a project page but aren't ready to show it publicly, add `published: false`:

```yaml
---
title: "My New Project"
status: active
published: false
---
```

This hides the project from the Projects listing page and from member profile pages. Remove the line or change it to `published: true` when you're ready to publish.

---

## 8. Publications

### Where to edit

All publications live in a single file: **`_data/publications.yaml`**

Unlike members and projects (which each have their own file), publications are all listed together in this one YAML file.

### Publication fields

| Field | Required? | Description | Example |
|-------|-----------|-------------|---------|
| `id` | **Yes** | Unique identifier (use a short descriptive slug) | `eco-vis-literacy-2026` |
| `title` | **Yes** | Full paper title | `"From Charts to Context: An Ecological View of Visualization Literacy"` |
| `authors` | **Yes** | List of author names | See example below |
| `venue` | **Yes** | Conference or journal name | `"CHI 2026 Workshop on Data Literacy"` |
| `year` | **Yes** | Publication year | `2026` |
| `type` | **Yes** | One of: `paper`, `workshop`, `poster`, `thesis`, `preprint` | `workshop` |
| `projects` | No | List of project slugs this pub belongs to | `[eco-vis]` |
| `pdf` | No | URL to the PDF | `https://example.com/paper.pdf` |
| `doi` | No | DOI URL | `https://doi.org/10.1145/...` |
| `code` | No | URL to a code repository | `https://github.com/infovisions/...` |
| `award` | No | Award text, if any | `Best Paper Award` or `Honorable Mention` |
| `thumb` | No | Thumbnail image path | `images/projects/eco-vis/eco-vis-literacy.png` |

### Linking publications to projects

The `projects` field is a list of project slugs. When a publication includes a project slug, it automatically appears in the "Publications" section on that project's detail page.

For example, if a project file is `_projects/eco-vis.md`, its slug is `eco-vis`. Adding `eco-vis` to a publication's `projects` list links them:

```yaml
projects:
  - eco-vis
```

A publication can belong to multiple projects:

```yaml
projects:
  - eco-vis
  - career-values
```

### Complete example

Add new entries at the **bottom** of `_data/publications.yaml`:

```yaml
- id: eco-vis-literacy-2026
  title: "From Charts to Context: An Ecological View of Visualization Literacy"
  authors:
    - Frida Mudsam
    - Evan M. Peck
  venue: "CHI 2026 Workshop on Data Literacy"
  year: 2026
  type: workshop
  projects:
    - eco-vis
  pdf:
  doi:
  code:
  award:
  thumb: images/projects/eco-vis/eco-vis-literacy.png
```

> **Tip:** It's fine to leave fields like `pdf`, `doi`, `code`, and `award` blank. Just include the field name with nothing after the colon. You can fill them in later when the links become available.

---

## 9. News Items

### Where to edit

News items live in **`_data/news.yaml`**. They appear on the homepage under "Recent News." The homepage shows the 6 most recent items, sorted by date.

### News fields

| Field | Required? | Description | Example |
|-------|-----------|-------------|---------|
| `date` | **Yes** | Date in `YYYY-MM-DD` format | `2026-03-01` |
| `text` | **Yes** | The news text (Markdown supported — you can include **bold**, *italic*, and [links](https://example.com)) | See example below |

### Complete example

Add new items at the **top** of the file (so the most recent item is first):

```yaml
- date: 2026-03-01
  text: "Frida Mudsam's workshop paper was accepted to the [ACM CHI 2026 Workshop on Data Literacy](https://data-literacy-workshop.github.io/CHI26/) in Barcelona, Spain"

- date: 2026-01-15
  text: "Evan Peck launches a new course at CU Boulder — *Communicative Visualization*"
```

> **Tip:** Make sure the `text` value is wrapped in quotes (`"..."`) if it contains colons, special characters, or Markdown links. This prevents YAML parsing errors.

---

## 10. External Collaborators

### When to use

Collaborators are people **outside** the lab who work with us on projects — for example, co-PIs at other universities. They don't get their own profile page on the site, but they appear as named portraits on project detail pages and as small avatar photos on project cards.

### Where to edit

Each collaborator has their own file in **`_collaborators/`**.

### Collaborator photo

Upload their photo to **`images/collaborators/`** using the naming convention `firstname-lastname-photo.jpg`.

### Frontmatter fields

| Field | Required? | Description | Example |
|-------|-----------|-------------|---------|
| `name` | **Yes** | Full name | `Darakhshan Mir` |
| `group` | **Yes** | Must be `collaborator` | `collaborator` |
| `role` | **Yes** | Must be `collaborator` | `collaborator` |
| `description` | **Yes** | Their title/position | `"Associate Professor of Computer Science"` |
| `affiliation` | **Yes** | Their institution | `"Bucknell University"` |
| `website` | **Yes** | Link to their homepage (this is where their name links to on project pages) | `"https://www.bucknell.edu/fac-staff/darakhshan-mir"` |
| `image` | **Yes** | Path to their photo | `images/collaborators/darakhshan-mir-photo.jpg` |

### Complete example

Here is a full collaborator file (`_collaborators/darakhshan-mir.md`):

```yaml
---
name: Darakhshan Mir
group: collaborator
role: collaborator
description: "Associate Professor of Computer Science"
affiliation: "Bucknell University"
website: "https://www.bucknell.edu/fac-staff/darakhshan-mir"
image: images/collaborators/darakhshan-mir-photo.jpg
---
```

> **Note:** Collaborator files have **no content after the frontmatter** — just the YAML block. All their information is in the fields above.

### Using collaborators in projects

Once you've created a collaborator file, you can reference them in project files using their slug (the filename without `.md`):

```yaml
# In a project file
pi:
  - evan-peck
  - darakhshan-mir     # ← This looks up _collaborators/darakhshan-mir.md
```

---

## 11. Images

### Where to put images

| Image type | Folder | Naming convention |
|-----------|--------|-------------------|
| Member photos | `images/members/` | `firstnamelastinitial-photo.jpg` (e.g., `janed-photo.jpg`) |
| Project images | `images/projects/your-project-slug/` | Descriptive name (e.g., `framework-diagram.png`) |
| Collaborator photos | `images/collaborators/` | `firstname-lastname-photo.jpg` |
| Funder logos | `images/funding/` | `funder-name.svg` or `.png` |

### Recommendations

- **Member/collaborator photos:** Square or near-square crop works best (they display as circles). Aim for at least 400x400 pixels.
- **Project card thumbnails:** Displayed at 16:9 aspect ratio. Landscape-oriented images work best.
- **File size:** Keep images under 500 KB when possible. Compress large photos using a free tool like [Squoosh](https://squoosh.app/).
- **Formats:** `.jpg` for photos, `.png` for diagrams/screenshots, `.svg` for logos/icons.

### Referencing images

**In YAML frontmatter** (no leading slash):

```yaml
image: images/members/janed-photo.jpg
```

**In Markdown content** (leading slash required):

```markdown
![Description of the image](/images/projects/eco-vis/diagram.png)
```

> **Important:** When referencing images in the body of a Markdown file, you **must** include the leading `/` before `images/`. In YAML frontmatter, you do **not** include the leading `/`. Getting this wrong is one of the most common causes of broken images.

---

## 12. Quick Reference

| I want to... | Edit this file/folder | Key fields |
|--------------|----------------------|------------|
| Update my profile | `_members/your-name.md` | `name`, `image`, `role`, `links` |
| Add a new lab member | Create `_members/firstname-lastname.md` | `name`, `image`, `role` |
| Add a project | Create `_projects/short-name.md` | `title`, `status`, `short_description` |
| Hide a draft project | Edit the project's `.md` file | Set `published: false` |
| Add a publication | Edit `_data/publications.yaml` | `id`, `title`, `authors`, `venue`, `year`, `type` |
| Link a publication to a project | Edit `_data/publications.yaml` | Add project slug to `projects` list |
| Add a news item | Edit `_data/news.yaml` | `date`, `text` |
| Add an external collaborator | Create `_collaborators/firstname-lastname.md` | `name`, `group`, `role`, `website`, `image` |
| Upload a photo | Upload to the appropriate `images/` subfolder | |

---

## Common Mistakes and How to Fix Them

### YAML indentation errors

YAML is very sensitive to indentation. Always use **spaces** (not tabs), and keep items at the same level lined up.

```yaml
# WRONG — inconsistent indentation
lead:
  - frida-mudsam
    - evan-peck        # ← This is indented too far

# RIGHT
lead:
  - frida-mudsam
  - evan-peck
```

### Missing quotes around special characters

If your text contains colons (`:`), brackets, or other special YAML characters, wrap the whole value in quotes:

```yaml
# WRONG — the colon breaks the YAML
title: AI & Ethics: A New Framework

# RIGHT
title: "AI & Ethics: A New Framework"
```

### Broken images

If an image isn't showing up, check these things:
1. **Is the file actually uploaded?** Look in the correct `images/` subfolder on GitHub.
2. **Is the path correct?** Check for typos in the filename or folder name.
3. **Leading slash rule:** In Markdown content, image paths need a leading `/`. In YAML frontmatter, they don't.

```yaml
# In YAML frontmatter — NO leading slash
image: images/members/janed-photo.jpg

# In Markdown body — YES leading slash
![Photo](/images/members/janed-photo.jpg)
```

### Changes not appearing

After committing, wait 1–2 minutes for GitHub Actions to rebuild the site. You can check the build status by going to the [Actions tab](https://github.com/infovisions/infovisions.github.io/actions) in the repository — a green checkmark means the build succeeded.

If the build fails (red X), click on the failed run to see what went wrong. The most common cause is a YAML syntax error (bad indentation or missing quotes).
