# Zoox Job Requisition Tool

A lightweight, browser-based tool for Zoox recruiters to quickly build and preview job descriptions. No backend, no login, no installation required — runs entirely in the browser.

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git
```

### 2. Navigate into the project folder

```bash
cd YOUR-REPO-NAME
```

### 3. Open the tool

No build step or server needed. Just open the file directly in your browser:

```bash
# macOS
open index.html

# Windows
start index.html

# Linux
xdg-open index.html
```

Or drag and drop `index.html` into any browser window.

---

## Deploying to GitHub Pages

### 1. Push to GitHub

```bash
git add .
git commit -m "Initial commit"
git push origin main
```

### 2. Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages**
3. Under **Source**, select `main` branch and `/ (root)`
4. Click **Save**

### 3. Access your live URL

After about 60 seconds your tool will be live at:

```
https://YOUR-USERNAME.github.io/YOUR-REPO-NAME
```

Share this URL with your team — anyone with the link can open and use it instantly, no account required.

---

## How to use the tool

1. Select a **Job Group** from the dropdown — this clears all fields and auto-fills role-specific content
2. Enter a **Job Title** — this becomes the heading of the generated job description
3. Review and edit the auto-filled **Job Description Intro**, **In This Role You Will**, **Qualifications**, and **Bonus Qualifications** fields
4. Fill in **Hiring Manager**, **Location**, and **Job Level Range**
5. Add any internal notes to **Special Call Out** (this field does not appear in the generated JD)
6. Fill in the **Interview Panel** fields for each stage
7. Click **Preview JD** to generate the formatted job description on the right panel
8. Use the **copy** button next to any section to copy it individually, or **Copy to clipboard** to copy the full JD

---

## Form fields reference

| Field | Description | Appears in JD |
|---|---|---|
| Job Group | Dropdown — triggers auto-fill and clears all fields | No |
| Job Title | Free text — used as the JD heading | Yes |
| Job Description Intro | Opening paragraph | Yes |
| Hiring Manager | Free text | Metadata only |
| Location | Dropdown | Metadata only |
| Job Level Range | Two fields, e.g. L3 to L5 | Metadata only |
| Special Call Out | Internal recruiter notes | No |
| In This Role You Will | Responsibilities (bullet points) | Yes |
| Qualifications | Max 4–5 bullet points | Yes |
| Bonus Qualifications | Max 3 bullet points | Yes |
| Initial Interview | Interview panel — stage 1 | Yes |
| Language | Interview panel — stage 2 | Yes |
| Onsite Panel | Interview panel — stage 3 | Yes |
| Exec Review | Interview panel — stage 4 | Yes |

---

## Auto-fill support

| Job Group | Intro | Responsibilities | Qualifications | Bonus Quals |
|---|---|---|---|---|
| Operational Tools IC | ✓ | ✓ | ✓ | ✓ |
| Operational Tools EM | ✓ | ✓ | ✓ | — |
| Maestro IC | — | — | — | — |
| Maestro EM | — | — | — | — |
| Site Reliability Engineering IC | — | — | — | — |
| Site Reliability Engineering EM | — | — | — | — |
| QA IC | — | — | — | — |
| QA EM | — | — | — | — |

Groups marked — have no auto-fill yet. See below for how to add content.

---

## Adding auto-fill content for new job groups

Open `index.html` and find the `AUTOFILL` object in the `<script>` section. Add or update an entry:

```js
'maestro-ic': {
  intro: `Your intro paragraph here...`,
  role: `• Responsibility one\n• Responsibility two\n• Responsibility three`,
  qualifications: `• Qualification one\n• Qualification two\n• Qualification three`,
  bonus: `• Bonus qualification one\n• Bonus qualification two`
},
```

Key names map to the dropdown `value` attributes:

| Dropdown value | Job Group |
|---|---|
| `ops-ic` | Operational Tools IC |
| `ops-em` | Operational Tools EM |
| `maestro-ic` | Maestro IC |
| `maestro-em` | Maestro EM |
| `sre-ic` | Site Reliability Engineering IC |
| `sre-em` | Site Reliability Engineering EM |
| `qa-ic` | QA IC |
| `qa-em` | QA EM |

---

## Updating the tool

To pull the latest changes from the repository:

```bash
git pull origin main
```

To publish your own changes:

```bash
git add .
git commit -m "Describe your change here"
git push origin main
```

GitHub Pages will automatically update within about 60 seconds of a push.

---

## File structure

```
index.html    — the entire application (HTML + CSS + JS, no dependencies)
README.md     — this file
```

---

## Notes

- No data is stored or transmitted — everything runs in the user's browser
- Each user session is fully independent — multiple people can use the tool simultaneously
- Refreshing or closing the tab resets all fields — there is no saved state between sessions
- The **Special Call Out** field is for internal notes only and never appears in the generated JD
- Switching job groups clears all previously entered data
