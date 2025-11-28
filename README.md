# Persistent Twin – Technical Explorer

**Persistent Twin** is the "character sheet" (Save file) for a modern worker inside our wider **Aspect Engine**.

Instead of a static profile or a list of completed courses, the Twin is a **live, data-driven view** of how someone is actually performing: what they’re good at, where they’re struggling, and what the system is going to do about it next.

This repo contains a **front-end prototype** of the Twin’s main UI panel (Just the “Middle Window”) There is a 3-layered Window one aligning left the other to the right.

---

## 1. How it fits into Aspect

Aspect has three main layers:

1. **Aspect Engine (Progression Engine)**  
   - Keeps a long-lived mastery profile for each user  
   - Chooses the **next mission** based on gaps, streaks, and difficulty (“challenge vs reinforce”)  
   - Works first on data/digital skills (Numeracy, Spreadsheets, SQL & Automation) (Subjects are easily upgradeable in our upgrade patch)

2. **Veil (Guide & UI Layer)**  
   - LLM-powered assistant that receives explains tasks, gives hints, and marks missions  
   - Reads from:
     - the user’s mastery profile (what they can/can’t do yet),
     - a **content/lore atlas** of missions and examples (authored by subject-matter experts),
     - the current UI state (what mission the user is on)
   - Translates engine decisions into humane, gentle coaching (“We saw you struggled with percentages, so we’re giving you a simpler cleaning task to rebuild confidence.”)

3. **Persistent Twin (This Repo)**  
   - Sits in the **middle of the dashboard**, between:
     - the Skill Map (left) and
     - the Mission Queue / Quest Log (right)
   - Visualises:
     - **Skill mastery** per branch (XP, level, recent success, trend)
     - **Momentum** (streak, missions completed this week)
     - **Engine focus** (what the engine is trying to improve next, and why)

The long-term idea is that **educators / subject specialists** create mission packs (SQL, data cleaning, numeracy boosts, etc.).  
Those missions live in the content atlas; the Engine picks from them; Veil coaches through them; the Twin makes that whole process *visible, fair, and motivating* to the user.

---

## 2. What this prototype shows

This static HTML demo focuses on **the Twin itself**, not the whole product.

Key elements:

- **Interactive persona toggle**  
  Switch between:
  - *Analyst A-317 (veteran)* – strong numeracy, at-risk spreadsheets, untrained SQL  
  - *Analyst B-002 (rookie)* – weak foundations, no streak, needs very gentle missions  

- **Middle Window UI zones**
  - **Identity Header** – who this profile belongs to (role, site, avatar)
  - **Skill Mastery Cards** – per-branch XP, levels, success %, and risk tags (STABLE / AT RISK / NOT YET TRAINED)
  - **Streak Strip** – days active + missions this week
  - **Engine Focus Panel** – explains the next mission and cognitive mode  
    (e.g. “Try first, then hint” vs “Step-by-step guide”)
  - **Veil Coach Note** – a small, human-sounding explanation of *why* the system is doing what it’s doing

- **Engine Analytics Visualisation**
  - Radar chart: shows the “shape” of a user’s skills (Numeracy vs Spreadsheets vs SQL)
  - Scatter plot: shows how the Engine picks a task slightly above current competence (Zone of Proximal Development)

This is **not** the full product. It’s a **technical and UX explorer** of one key component:
> “How do we objectify competence and keep users engaged, without being cruel or opaque?”

---

## 3. Stack & Implementation Notes

- Pure **static HTML + Tailwind CSS (CDN)**  
- **Chart.js** for radar and scatter plots  
- No backend in this repo – data is mocked in the front-end
- Designed to be hosted via **GitHub Pages** as a simple, shareable artifact

You can view the live demo here:

> `https://caldari0.github.io/persistent-twin/`  


---

## 4. Intended audience

- **Developers / tech leads** – to understand the Twin’s data inputs and UI structure
- **Product / L&D / Ops stakeholders** – to see how Aspect would make performance feel more like a game and less like a mystery
- **Designers** – as a starting point for proper Figma or production UI work
