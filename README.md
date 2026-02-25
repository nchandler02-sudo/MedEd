# 🩺 MedEd Central

**Your Internal Medicine Command Center**

A gamified medical education hub for interns, residents, and fellows. Each specialty is a standalone learning app with ABIM-style questions, micro-quizzes, progress tracking, and a full gamification system — all mapped to the official ABIM Internal Medicine exam blueprint.

---

## 🗺️ What's Inside

### 📚 ABIM Board Review (16 Specialties)

| Specialty | ABIM Weight | Status |
|---|---|---|
| ❤️ Cardiology | 14% | ✅ Live |
| 🫁 Pulmonology | 9% | 🔜 Coming Soon |
| 🍽️ Gastroenterology & Hepatology | 9% | 🔜 Coming Soon |
| 🦠 Infectious Disease | 9% | 🔜 Coming Soon |
| 🧪 Endocrinology & Metabolism | 9% | 🔜 Coming Soon |
| 🦴 Rheumatology | 9% | 🔜 Coming Soon |
| 🫘 Nephrology | 6% | 🔜 Coming Soon |
| 🩸 Hematology | 6% | 🔜 Coming Soon |
| 🎗️ Oncology | 6% | 🔜 Coming Soon |
| 🧠 Neurology | 4% | 🔜 Coming Soon |
| 🧩 Psychiatry | 4% | 🔜 Coming Soon |
| 🔬 Dermatology | 3% | 🔜 Coming Soon |
| 👴 Geriatrics & Palliative Care | 3% | 🔜 Coming Soon |
| 🤰 Women's Health & OB/GYN | 3% | 🔜 Coming Soon |
| 🌿 Allergy, Immunology & ENT | 4% | 🔜 Coming Soon |
| ⚖️ Foundations (Ethics, Epi, QI) | 2% | 🔜 Coming Soon |

### 🏥 Clinical Rotation Toolkit (3 Modules)

| Module | Status |
|---|---|
| 🏥 Critical Care / ICU | 🔜 Coming Soon |
| 🌙 Night Float / Cross-Cover | ✅ Live |
| 📋 Intern Survival Guide | 🔜 Coming Soon |

---

## 🚀 Quick Start

### Deploy to GitHub Pages

1. **Create a repo** named `your-username.github.io` (or any repo with Pages enabled)

2. **Clone and add files:**
   ```bash
   git clone https://github.com/your-username/your-username.github.io.git
   cd your-username.github.io
   ```

3. **Add the hub page:** Place `index.html` in the repo root

4. **Add specialty apps:** Each specialty gets its own folder:
   ```
   your-repo/
   ├── index.html              ← Hub page
   ├── .nojekyll               ← CRITICAL (see below)
   ├── cardiology/
   │   ├── index.html          ← Cardiology app
   │   ├── .nojekyll
   │   ├── data.json
   │   └── topics/
   │       ├── manifest.json
   │       ├── acute-heart-failure.md
   │       └── ...
   ├── night-float/
   │   ├── index.html
   │   ├── .nojekyll
   │   ├── data.json
   │   └── topics/
   │       └── ...
   └── (more specialties...)
   ```

5. **Push and enable Pages:**
   ```bash
   git add .
   git commit -m "Initial deploy"
   git push
   ```
   Then go to **Settings → Pages → Deploy from branch → main → / (root) → Save**

6. **Visit** `https://your-username.github.io` — your hub is live!

### Local Development

```bash
# Using Node
npx serve .

# Using Python
python3 -m http.server 8000
```

Then open `http://localhost:8000` (or `:3000` for `npx serve`).

---

## ⚠️ Critical: The `.nojekyll` File

GitHub Pages runs Jekyll by default, which converts `.md` files into HTML pages. This breaks the specialty apps because they fetch raw markdown.

**You MUST add an empty `.nojekyll` file to the repo root.**

```bash
touch .nojekyll
git add .nojekyll
git commit -m "Add .nojekyll to prevent Jekyll processing"
git push
```

**How to tell if it's missing:** Open your browser console. If you see `[APP] Got HTML instead of MD`, Jekyll is processing your markdown files.

---

## 🔧 How to Add a New Specialty

### Step 1: Build the specialty app

Use the master build prompt to generate a specialty app. This produces:
- `index.html` — the complete gamified app
- `data.json` — parsed topic content
- `topics/` folder with `.md` files and `manifest.json`
- `pretest.json` and `posttest.json` — assessment files

### Step 2: Add it to the repo

```bash
mkdir nephrology
# Place all generated files in the nephrology/ folder
```

### Step 3: Activate it in the hub

Open the root `index.html` and find the specialty in the `BOARD_TOPICS` array:

```javascript
{
  title: "Nephrology",
  emoji: "🫘",
  url: "./nephrology/",    // ← path to the folder
  live: true,              // ← change from false to true
  // ...
}
```

### Step 4: Push

```bash
git add .
git commit -m "Add Nephrology module"
git push
```

That's it — the hub will now link to the live app.

---

## 🎨 Features

- **Dark/Light theme** — Night Shift (dark) and Day Shift (light) toggle, synced to localStorage
- **Search** — Filter specialties instantly (press `/` to focus)
- **ABIM exam weights** — Each board review card shows the percentage of the certification exam
- **Fully responsive** — Works on phones, tablets, and desktops
- **Zero dependencies** — Pure HTML, CSS, and vanilla JavaScript
- **Single-file hub** — The entire homepage is one `index.html`

---

## 📁 Repo Structure Reference

```
your-repo/
│
├── index.html                  ← Hub homepage
├── .nojekyll                   ← Prevents Jekyll (REQUIRED)
├── README.md                   ← This file
│
├── cardiology/                 ← Example specialty app
│   ├── index.html              ← Complete gamified app
│   ├── .nojekyll
│   ├── data.json               ← Parsed topic data
│   ├── pretest.json            ← Pre-test questions
│   ├── posttest.json           ← Post-test questions
│   └── topics/
│       ├── manifest.json       ← Topic file list
│       ├── acute-heart-failure.md
│       ├── atrial-fibrillation.md
│       └── ... (20 .md files)
│
├── night-float/                ← Another specialty app
│   └── (same structure)
│
└── (more specialties...)
```

---

## 🤝 Contributing

Each specialty app is self-contained. To contribute a new module:

1. Pick an unclaimed specialty from the table above
2. Use the master build prompt to generate the app
3. Test locally with `npx serve .`
4. Submit a PR adding your specialty folder

---

## 📋 Roadmap

- [x] Hub homepage with all 19 specialties
- [x] Night Float / Cross-Cover module
- [x] Cardiology module
- [ ] Pulmonology
- [ ] GI & Hepatology
- [ ] Infectious Disease
- [ ] Endocrinology
- [ ] Rheumatology
- [ ] Nephrology
- [ ] Hematology
- [ ] Oncology
- [ ] Neurology
- [ ] Psychiatry
- [ ] Dermatology
- [ ] Geriatrics & Palliative Care
- [ ] Women's Health & OB/GYN
- [ ] Allergy, Immunology & ENT
- [ ] Foundations
- [ ] Critical Care / ICU
- [ ] Intern Survival Guide

---

## 📄 License

This project is for educational purposes. Medical content should be reviewed by qualified professionals before clinical use.

---

<p align="center">
  Built with ♥ for medical trainees everywhere
</p>
