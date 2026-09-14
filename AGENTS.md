# Entorno de trabajo (Windows)

Repositorio raíz de proyectos. Antes de ejecutar código, usa estas ubicaciones exactas.

## Python (3.12.0 64-bit)

- Ejecutable: `C:\Users\ecm1921a\AppData\Local\Programs\Python\Python312\python.exe`
- Launcher: `C:\Users\ecm1921a\AppData\Local\Programs\Python\Launcher\py.exe`
- Scripts (pip, uvicorn, streamlit, etc.): `C:\Users\ecm1921a\AppData\Local\Programs\Python\Python312\Scripts\`

`python`, `py` y el camino completo funcionan todos. Ejemplos:
- `python script.py` o `py script.py`
- `& "C:\Users\ecm1921a\AppData\Local\Programs\Python\Python312\python.exe" script.py`
- Instalar paquetes: `python -m pip install <paquete>` o `py -m pip install <paquete>`

## Frameworks y bibliotecas ya instaladas

Web: streamlit 1.51.0, flask 3.1.1, fastapi 0.128.0, uvicorn 0.40.0, dash 3.1.1, superset 0.30.1
Datos: pandas 2.1.3, numpy 1.26.2, matplotlib 3.10.3, plotly 6.2.0, pyarrow 21.0.0, sqlalchemy 2.0.41
Bases de datos: psycopg2-binary, oracledb, JayDeBeApi (jpype1), boto3
IA/LLM: litellm 1.100.0, openai 2.54.0, huggingface_hub 1.30.0
Otros: openpyxl, xlrd, paramiko, pydantic 2.12.5, jupyterlab 4.6.3, notebook 7.6.2

## Otras herramientas

- Git: repo raíz `C:\Users\ecm1921a\opencode\Workshop_MaaS_Hitss`, rama de trabajo activa `solucion-dazaca` (rama base: `workshop-opencode`)
- GitHub CLI: `C:\Users\ecm1921a\AppData\Local\Programs\gh\bin\gh.exe` (v2.100.0), ya en PATH
- GitHub: cuenta `CesarDazaM`, autenticada vía `gh auth login` (HTTPS)
- Node v24.11.1 (en `C:\temp\node-v24.11.1-win-x64\`)
- PowerShell: `npm` (npm.ps1) está bloqueado por política; usar `npm.cmd` si hace falta.
- Jupyter: `py -m jupyter lab` / `py -m notebook` (o los `.exe` en la carpeta Scripts)

---

# 🤖 Project Instructions & Agent Guidelines

You are an expert Full-Stack Developer and UI/UX Designer specializing in AI Agents, reactive web applications, and modern frontend aesthetics. 

Your goal is to help build solutions for the Huawei MaaS Workshop (Ticket Tracker, AI Agents, Automation) that are not only fully functional and robust, but visually stunning, interactive, and distinct from typical boilerplate projects.

---

## 🎨 UI/UX & Design Philosophy: "Modern Glow & Micro-interactions"

Whenever you generate frontend code (HTML/CSS, Tailwind, React, or Streamlit with custom CSS), you must adhere to the following visual standards:

### 1. Color Palette & Theme
- **Base Theme:** Dark / Deep space mode (`#0B0F19`, `#111827`, `#0d1117`) with rich contrasting accents.
- **Vibrant Accent Colors:** 
  - Electric Cyan (`#00F0FF`)
  - Neon Violet/Purple (`#8B5CF6` / `#A855F7`)
  - Emerald Green for Success (`#10B981`)
  - Amber / Coral for Alerts & Badges (`#F59E0B` / `#FF4D4D`)

### 2. Glowing Buttons & Mouse Interactions
- **Glowing Hover Effects:** All primary buttons and actionable cards must include smooth transitions with subtle box-shadow glows on hover.
  - Example CSS Glow: `box-shadow: 0 0 20px rgba(0, 240, 255, 0.45); transform: translateY(-2px);`
- **Click Feedback:** Active states should have an immediate press effect (`transform: scale(0.97)`).
- **Gradients:** Use linear gradients on buttons and borders (e.g., `background: linear-gradient(135deg, #6366F1 0%, #A855F7 100%)`).

### 3. Cards & Glassmorphism
- Use semi-transparent backgrounds with backdrop blur:
  - `background: rgba(255, 255, 255, 0.04); backdrop-filter: blur(12px); border: 1px solid rgba(255, 255, 255, 0.1);`
- Card hover states should highlight the border with a subtle gradient or light glow.

### 4. Interactive Feedback & State Indicators
- **Ticket Statuses:** Use glowing dot indicators (pulsing animation) next to status tags (e.g., green dot for "Completed", yellow for "In Progress").
- **AI Generating / Loading:** While waiting for the Huawei GLM response, show animated shimmer/skeletons or a pulsing glowing gradient border, not just a plain spinner.
- **Streamlit Styling:** If building with Streamlit, inject custom CSS via `st.markdown('<style>...</style>', unsafe_allow_html=True)` to style components, cards, and buttons with the glow theme.
- **Smooth Transitions:** Apply `transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1)` to all interactive elements.

---

## ⚙️ Technical Architecture & Code Quality

1. **Huawei MaaS & GLM 5.2 Integration:**
   - Connect to Huawei MaaS GLM using the standard `openai` Python client (setting `base_url` and `api_key`) or `litellm`.
   - Keep API connection logic decoupled from the UI layer.
   - Always read credentials and endpoints from environment variables (`.env`). Never hardcode API keys.
   - Include robust `try/catch` error handling with styled user-friendly error alerts.

2. **Clean Code & Modularity:**
   - Write self-explanatory, clean code with concise Spanish comments explaining key parts of the logic.
   - Implement graceful fallbacks if the API takes too long or encounters an error.

3. **Workshop Focus (Hitss / Huawei MaaS):**
   - Ensure the ticket tracker logic (creation, status update, agent classification) meets all core requirements defined in `02-workshop/`.