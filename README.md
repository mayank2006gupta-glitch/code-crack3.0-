# CampusCare – Campus Complaint Management System (CCMS)
> **Comprehensive Campus Problem & Complaint Resolution Platform**  
> *Track. Prioritize. Resolve.*

Built with **pure semantic HTML5, modern CSS3, and vanilla JavaScript (ES6+) with LocalStorage persistence**. Zero heavyweight dependencies or complex backend setup required—runs immediately in any web browser or via VS Code Live Server.

Designed specifically to match the modern enterprise dashboard aesthetic (**royal blue sidebar with concave active tab curve, real-time KPI metrics, circular service level donut gauge, dual-trend SVG curves, and interactive complaint management**).

---

## 📁 Project Structure

```
Campus-Complaint-Management/
├── index.html     # Semantic dashboard markup, SVG charts, modals & controls
├── style.css      # Custom UI theme, curved sidebar tabs, animations & status badges
├── script.js      # Priority queue algorithm, LocalStorage DB, filters & reactivity
└── README.md      # Comprehensive competition guide, test cases & judge Q&A
```

---

## 🚀 How to Run the Project

1. Open the project folder in **VS Code**:
   ```
   C:\Users\hp\.gemini\antigravity\scratch\Campus-Complaint-Management
   ```
2. Double-click [`index.html`](file:///C:/Users/hp/.gemini/antigravity/scratch/Campus-Complaint-Management/index.html) to open directly in Google Chrome, Microsoft Edge, or Firefox.
3. *(Alternative)* Right-click `index.html` in VS Code and choose **Open with Live Server**.

---

## 🧮 The Priority Urgency Algorithm (Analytical Challenge - 25 Marks)

### Formula:
$$\text{Urgency Score} = \text{Category Weight} + \left\lfloor\frac{\text{Hours Pending}}{24}\right\rfloor$$

Where:
- $\lfloor x \rfloor$ is the floor function (greatest integer $\le x$).
- **Category Weights** (defined by competition problem statement):
  - **Laboratory**: `3`
  - **Wi-Fi**: `2`
  - **Hostel**: `2`
  - **Classroom**: `1`
- **Hours Pending**: Elapsed hours since complaint was raised: `(Date.now() - createdAt) / (1000 * 60 * 60)`.
- **Aging Factor**: For every complete 24-hour cycle an issue remains unresolved, its urgency score increases by `+1`.

### Strict Specification Rule:
> **Resolved complaints are permanently excluded from the priority queue**, regardless of their mathematical urgency score.

### Tie-Breaking Hierarchy:
1. **Highest Urgency Score first** (descending order).
2. **Older complaint first** if scores are equal (larger hours pending).
3. **Smaller Complaint ID first** if both score and age are equal (`C01` before `C02`).

### Initial PDF Test Dataset Verification:
| ID | Category | Age (Hours) | Weight | Bonus $\lfloor\text{Age}/24\rfloor$ | Mathematical Score | Status | Queue Position | Reason |
|:---|:---|:---:|:---:|:---:|:---:|:---:|:---:|:---|
| **C03** | Classroom | 72h | 1 | 3 | **4** | Raised | **Rank #1** | Highest score (4) & oldest (72h) |
| **C01** | Wi-Fi | 48h | 2 | 2 | **4** | Raised | **Rank #2** | Same score (4), but younger (48h) |
| **C02** | Hostel | 8h | 2 | 0 | **2** | In Progress | **Rank #3** | Score 2 |
| **C04** | Laboratory | 24h | 3 | 1 | **4** | **Resolved** | **EXCLUDED** | **Strict rule: Resolved excluded** |

---

## 🌟 Key Features & Marks Breakdown

### 1. Complaint Workflow & Validation (30 Marks)
- **Submit Complaint Form**: Clean modal form with Category dropdown, Description textarea, Student Name, and Room/Location.
- **Strict Validation**: Prevents blank categories, empty descriptions, or descriptions shorter than 5 characters.
- **Unique ID Generation**: Automatically generates sequential alphanumeric IDs (`C01`, `C02`, `C03`, `C04`, `C05`...) avoiding duplicates even if items are deleted.
- **Status Lifecycle**: Supports three continuous stages:
  $$\text{Raised} \longrightarrow \text{In Progress} \longrightarrow \text{Resolved}$$
- Immediate toast confirmations on ticket creation and status transitions.

### 2. Search, Filters & Summary Statistics (20 Marks)
- **Real-Time Global Search**: Instant filtering across ID, category, student name, location, and description keywords.
- **Multi-Criteria Filtering**: Combine Category (`Wi-Fi`, `Hostel`, `Classroom`, `Laboratory`) and Status (`Raised`, `In Progress`, `Resolved`) seamlessly.
- **Sort Orders**: Sort by Newest, Oldest, Highest Urgency Score, or Complaint ID.
- **Dynamic KPI Cards**:
  - **Pending Count** (Raised tickets awaiting attention)
  - **In Progress Count** (Currently assigned and being worked on)
  - **Solved Count** (Resolved tickets)
  - **Service Level Gauge** (Interactive circular SVG ring showing resolution percentage)
  - **Feedback Rating** (4.6 / 5 campus satisfaction)

### 3. Priority Logic & Visualization (25 Marks)
- **Top 3 Priority Queue Spotlight**: Prominently displayed cards with Rank #1, #2, #3 badges, urgency scores, age indicators, and quick action buttons.
- **Interactive Formula Inspector**: A dedicated modal explaining the formula and an interactive calculator where judges can input custom categories and hours to test live!
- **Dynamic Re-ranking**: When Rank #1 is marked Resolved, it vanishes from the queue immediately and the next highest complaint moves up!

### 4. Data Handling & Persistence (15 Marks)
- **Browser LocalStorage**: Data survives browser refresh and tab closures.
- **Reset to Sample Dataset**: Instant one-click button in sidebar footer to restore the exact PDF dataset (`C01` to `C04`) for judges.
- **Export to CSV**: Download all complaint records as `campuscare_complaints.csv`.
- **Graceful Empty State**: Friendly placeholder when zero complaints match search filters.

### 5. UI/UX & Aesthetics (10 Marks)
- Matches the uploaded GIS Enterprise Dashboard layout:
  - Deep royal blue navigation sidebar with curved active tab cutout (`::before` / `::after` inverted border-radius).
  - Dual-trend smooth SVG line chart with hover tooltips.
  - Category distribution horizontal progress bars.
  - Custom pill badges for status (`Raised` blue outline, `In Progress` amber outline, `Closed` solid green).

---

## 🎤 Judge Q&A Cheat Sheet

| Question | Winning Answer |
|:---|:---|
| **Q1. What problem does your project solve?** | *"CampusCare provides a unified platform where students report issues and administrators track resolution. Crucially, instead of handling complaints randomly or by arrival order, our mathematical priority algorithm ensures critical and long-pending complaints are tackled first."* |
| **Q2. How is the Urgency Score calculated?** | *"We use: $\text{Urgency Score} = \text{Category Weight} + \lfloor\text{Hours Pending} / 24\rfloor$. Laboratory has weight 3, Wi-Fi 2, Hostel 2, Classroom 1. For every 24 hours an issue remains unresolved, it earns +1 bonus point. Resolved issues are strictly excluded."* |
| **Q3. How do you resolve ties between complaints?** | *"We use a 3-tier tie-breaking rule: 1) Highest urgency score first, 2) Older complaint first (larger pending hours), 3) Smaller Complaint ID lexicographically."* |
| **Q4. Why did you choose LocalStorage over an external database?** | *"For competition requirements, LocalStorage provides immediate zero-latency persistence without external server setup, making the application 100% portable, reliable during live evaluation, and easy to run on any computer."* |
| **Q5. What happens when a complaint is marked Resolved?** | *"Its status changes to Resolved, the counters and resolution percentage update, and it is instantly purged from the Top 3 Priority Queue."* |
