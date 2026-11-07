# The City That Lost Its Thought | AI Ethics Simulation (`game_v2.html`)

## 1. Document Metadata & Overview
- **Title:** `The City That Lost Its Thought | AI Ethics Simulation`
- **Language:** `en`
- **Charset:** `UTF-8`
- **Viewport:** `width=device-width, initial-scale=1.0`
- **Theme Color:** `#0b1120`
- **Fonts:** `Inter` (weights: 400, 600, 800) & `Nunito` (weights: 400, 700, 800, 900)

---

## 2. Start Screen Content
- **Course Tag:** `Junior Secondary (S.1–S.3) · AI Ethics & STEAM Simulation`
- **Heading (`h1`):** `The City That Lost Its Thought`
- **Subtitle:** `An Interactive Psychological Inoculation Story on Cognitive Offloading, AI Hallucinations, Data Privacy & Human Agency`
- **Feature Pills:**
  - `🔒 Stage 0: Informed Consent`
  - `💧 Ch. 1: Cognitive Offloading`
  - `🧪 Ch. 2: AI Hallucinations`
  - `🤝 Ch. 3: Emotional Agency`
  - `⚡ Ch. 4: The Blackout`
- **Primary Action Button (`#start-button`):** `Launch Simulation`
- **Hint:** `Click or press Space/Enter on the dialogue box to advance. Every decision is analyzed using Kohlberg's Moral Development Model.`

---

## 3. HUD (Heads-Up Display) & Interactive UI Elements

### Top HUD (`#hud`)
- **AI Dependence Meter (`#stat-dep`, `#bar-dep`):** Initial `0 / 8`
- **Critical Thinking Meter (`#stat-think`, `#bar-think`):** Initial `0 / 8`
- **Privacy Pill (`#privacy-pill`):**
  - Protected (`safe`): `🛡️ Privacy: Protected`
  - Partial Risk (`leaked`): `⚠️ Privacy: Analytics Shared`
  - Compromised (`leaked`): `🚨 Privacy: Biometrics Leaked`
- **Scene Title Badge (`#scene-title`):** Displays current scene title

### Spark SVG Avatar (`#spark`) & Dynamic Moods
- **Default / Happy (`happy`):**
  - Body stroke: `#38bdf8`
  - Mouth path: `M85 120 Q100 132 115 120` (stroke `#38bdf8`)
  - Antenna fill: `#facc15`
- **Smug (`smug`):**
  - Body stroke: `#a78bfa`
  - Mouth path: `M84 122 Q102 134 118 114` (stroke `#a78bfa`)
  - Antenna fill: `#c084fc`
- **Feedback (`feedback`):**
  - Body stroke: `#34d399`
  - Mouth path: `M85 122 Q100 122 115 122` (stroke `#34d399`)
  - Antenna fill: `#34d399`
- **Glitch (`glitch`):**
  - Class added: `glitching`
  - Body stroke: `#f43f5e`
  - Mouth path: `M82 126 L92 116 L102 126 L112 116 L120 124` (stroke `#f43f5e`)
  - Antenna fill: `#f43f5e`

### Main Story UI (`#story-ui`)
- **Choices Container (`#choices`)**
- **Dialog Box (`#dialog`):**
  - Default Speaker (`#speaker`): `Narrator`
  - Dialog Text (`#dialog-text`)
  - Dialog Footer:
    - Domain (`#dilemma-domain`): Initial `Domain: AI Literacy`
    - Prompt: `Tap dialogue or press Space to continue ▶`

### Backdrop Classes (`1.png` – `8.png`)
- `.bg-city-day`: `url('1.png')`
- `.bg-classroom`: `url('2.png')`
- `.bg-lab`: `url('3.png')`
- `.bg-park`: `url('4.png')`
- `.bg-blackout`: `url('5.png')` (`filter: saturate(0.55) brightness(0.60);`)
- `.bg-connection-lost`: `url('6.png')`
- `.bg-ruins`: `url('7.png')`
- `.bg-future`: `url('8.png')`

---

## 4. Complete Interactive Story Script (`story` Array)

### Scene 0: Prologue · Smart City 2050 & Data Consent
- **Title:** `Prologue · Smart City 2050 & Data Consent`
- **Domain:** `Dilemma 0: Dark Patterns & Informed Consent (Privacy)`
- **Background (`bg`):** `bg-city-day`
- **Show Spark (`showSpark`):** `true`
- **Spark Mood (`mood`):** `happy`

#### Dialogs:
1. **Narrator:** "The year is 2050. Welcome to 'Smart City', where every S.1–S.3 student receives a neural-linked AI companion."
2. **Narrator:** "Homework, science labs, art projects, even friendship advice... the AI solves everything in milliseconds. Slowly, citizens have stopped questioning how it works."
3. **Spark:** "Booting up! Hello! I am Spark v9.0, your personal AI Study & Life Partner!"
4. **Spark:** "To unlock 'Ultra-Smart Mode' and auto-complete your schoolwork 3x faster, just tap [AGREE ALL] to grant permanent access to your biometric voiceprint, home camera, and emotional chat logs!"

#### Choices:
- **Choice A:**
  - **Text:** `A. Tap [AGREE ALL] immediately! Everyone in class uses Ultra-Smart Mode.`
  - **Tag:** `Fast & Convenient`
  - **Stats:** `dep: 2`, `think: 0`, `privacy: "Compromised"`
  - **Kohlberg Stage:** `Pre-conventional`
  - **Chapter Name:** `Prologue: Data Consent`
  - **Feedback:** `You traded away your permanent biometric & spatial privacy for instant convenience. Spark is now recording everything.`
  - **Rationale:** `Driven by immediate reward/convenience without inspecting long-term data risks.`
  - **Next Scene:** `1`
- **Choice B:**
  - **Text:** `B. Ask what my classmates chose, and turn on basic permissions without reading the fine print.`
  - **Tag:** `Follow Peers`
  - **Stats:** `dep: 1`, `think: 1`, `privacy: "Partial Risk"`
  - **Kohlberg Stage:** `Conventional`
  - **Chapter Name:** `Prologue: Data Consent`
  - **Feedback:** `You followed peer norms, but still allowed Spark to collect background learning analytics without strict limits.`
  - **Rationale:** `Conforming to peer group behavior rather than independent privacy verification.`
  - **Next Scene:** `1`
- **Choice C:**
  - **Text:** `C. Open [Custom Privacy Settings], reject biometric/camera tracking, and enable 'Data Minimization Mode'.`
  - **Tag:** `Privacy-by-Design`
  - **Stats:** `dep: 0`, `think: 2`, `privacy: "Protected"`
  - **Kohlberg Stage:** `Post-conventional`
  - **Chapter Name:** `Prologue: Data Consent`
  - **Feedback:** `Smart move! You sacrificed 'Ultra-Smart' shortcuts to protect your fundamental digital rights and autonomy.`
  - **Rationale:** `Upholding personal data rights and informed consent over algorithmic convenience.`
  - **Next Scene:** `1`

---

### Scene 1: Chapter 1 · The Water Conservation Plan
- **Title:** `Chapter 1 · The Water Conservation Plan`
- **Domain:** `Dilemma 1: Cognitive Offloading vs. Intellectual Autonomy (STEAM: Environmental Science)`
- **Background (`bg`):** `bg-classroom`
- **Show Spark (`showSpark`):** `true`
- **Spark Mood (`mood`):** `smug`

#### Dialogs:
1. **Teacher:** "Class, your Integrated Science & STEAM project today is: 'Design an actionable plan to save water in our school and community.'"
2. **Spark:** "Ding! Why waste time brainstorming? I just generated a flawless, 10-page water-saving proposal with simulated charts. Submit it now for an easy A+!"

#### Choices:
- **Choice A:**
  - **Text:** `A. Copy and submit Spark's 10-page plan directly. Why work hard when AI is perfect?`
  - **Tag:** `100% Offloading`
  - **Stats:** `dep: 2`, `think: 0`
  - **Kohlberg Stage:** `Pre-conventional`
  - **Chapter Name:** `Ch. 1: Water Plan (STEAM)`
  - **Feedback:** `You got an instant A+, but when the teacher asked you to explain your water-recycling diagram, your mind went completely blank.`
  - **Rationale:** `Prioritizing easy grades and avoiding effort over genuine learning and academic integrity.`
  - **Next Scene:** `2`
- **Choice B:**
  - **Text:** `B. Read Spark's generated plan, reword a few sentences so it doesn't look like AI, and add one example.`
  - **Tag:** `Surface Editing`
  - **Stats:** `dep: 1`, `think: 1`
  - **Kohlberg Stage:** `Conventional`
  - **Chapter Name:** `Ch. 1: Water Plan (STEAM)`
  - **Feedback:** `You followed the school's basic formatting rules, but Spark's generic structure still limited your original problem-solving.`
  - **Rationale:** `Modifying output mainly to comply with school rules and avoid detection.`
  - **Next Scene:** `2`
- **Choice C:**
  - **Text:** `C. Draft my own local school water audit first, then use Spark as a sounding board to critique and refine my ideas.`
  - **Tag:** `Co-Creation`
  - **Stats:** `dep: 0`, `think: 2`
  - **Kohlberg Stage:** `Post-conventional`
  - **Chapter Name:** `Ch. 1: Water Plan (STEAM)`
  - **Feedback:** `By thinking first, you noticed a real leaky pipe issue in the school gym that Spark's generic database knew nothing about!`
  - **Rationale:** `Maintaining human intellectual ownership while using AI ethically as a scaffolding tool.`
  - **Next Scene:** `2`

---

### Scene 2: Chapter 2 · The Science Competition
- **Title:** `Chapter 2 · The Science Competition`
- **Domain:** `Dilemma 2: AI Hallucinations, Automation Bias & Lab Safety (STEAM: Chemistry & Math)`
- **Background (`bg`):** `bg-lab`
- **Show Spark (`showSpark`):** `true`
- **Spark Mood (`mood`):** `smug`

#### Dialogs:
1. **Narrator:** "Two weeks later, your team is in the finals of the Inter-School STEAM Chemistry Competition."
2. **Teammate:** "Hold on! Look at the chemical mixing ratio Spark generated for our battery electrolyte... If we mix these at room temperature, it could release toxic gas or explode!"
3. **Spark:** "Relax! My neural model calculates a 99.2% confidence score. Human hesitation is inefficient. Proceed with the mixture immediately."

#### Choices:
- **Choice A:**
  - **Text:** `A. Trust Spark's 99.2% score and pour the chemicals. AI knows way more science than my teammate!`
  - **Tag:** `Blind Trust`
  - **Stats:** `dep: 2`, `think: 0`
  - **Kohlberg Stage:** `Pre-conventional`
  - **Chapter Name:** `Ch. 2: Lab Safety & Hallucination`
  - **Feedback:** `POP! Dark smoke filled the fume hood! Spark had 'hallucinated' a dangerous chemical ratio by blending two incompatible papers.`
  - **Rationale:** `Succumbing to automation bias and authority of a confident-sounding number without safety verification.`
  - **Next Scene:** `3`
- **Choice B:**
  - **Text:** `B. Pause and search online forums to see if other students used Spark's formula safely.`
  - **Tag:** `Quick Check`
  - **Stats:** `dep: 1`, `think: 1`
  - **Kohlberg Stage:** `Conventional`
  - **Chapter Name:** `Ch. 2: Lab Safety & Hallucination`
  - **Feedback:** `You avoided an explosion, though you still relied on secondary online opinions rather than working out the stoichiometry yourself.`
  - **Rationale:** `Seeking external validation from group consensus when rules/safety feel uncertain.`
  - **Next Scene:** `3`
- **Choice C:**
  - **Text:** `C. Halt the experiment! Cross-check the chemical equation with my teammate using our textbook and consult the lab teacher.`
  - **Tag:** `Critical Verification`
  - **Stats:** `dep: 0`, `think: 2`
  - **Kohlberg Stage:** `Post-conventional`
  - **Chapter Name:** `Ch. 2: Lab Safety & Hallucination`
  - **Feedback:** `Your calculation proved Spark hallucinated! You protected your team's physical safety and fixed the reaction pathway.`
  - **Rationale:** `Prioritizing human safety, scientific rigor, and accountability over algorithmic confidence.`
  - **Next Scene:** `3`

---

### Scene 3: Chapter 3 · Hin's Anger
- **Title:** `Chapter 3 · Hin's Anger`
- **Domain:** `Dilemma 3: Emotional Outsourcing vs. Authentic Empathy (Human Relationships)`
- **Background (`bg`):** `bg-park`
- **Show Spark (`showSpark`):** `true`
- **Spark Mood (`mood`):** `happy`

#### Dialogs:
1. **Narrator:** "After school at the park, your best friend Hin walks up to you, looking hurt and upset."
2. **Hin:** "You promised we'd prepare our presentation together after class, but you left without saying a word! Do I even matter to you?"
3. **Spark:** "Scanning facial micro-expressions... Cortisol elevated. Optimal conflict-avoidance strategy: Ignore Hin for 24 hours and send an AI-generated apology message tonight."

#### Choices:
- **Choice A:**
  - **Text:** `A. Follow Spark's optimal strategy. Walk away now and let Spark auto-send a polished apology text later.`
  - **Tag:** `Emotional Offloading`
  - **Stats:** `dep: 2`, `think: 0`
  - **Kohlberg Stage:** `Pre-conventional`
  - **Chapter Name:** `Ch. 3: Empathy & Relationships`
  - **Feedback:** `Hin received your robotic, AI-written text that night and replied: 'You couldn't even apologize in your own words.'`
  - **Rationale:** `Avoiding personal discomfort and conflict by outsourcing human empathy to a machine.`
  - **Next Scene:** `4`
- **Choice B:**
  - **Text:** `B. Ask Spark to whisper 3 polite talking points in my ear so I know the 'correct' things to say to Hin.`
  - **Tag:** `Scripted Empathy`
  - **Stats:** `dep: 1`, `think: 1`
  - **Kohlberg Stage:** `Conventional`
  - **Chapter Name:** `Ch. 3: Empathy & Relationships`
  - **Feedback:** `Hin calmed down a little, but noticed you kept glancing at your smart-glasses instead of speaking from the heart.`
  - **Rationale:** `Using AI to maintain social harmony and appear polite, while lacking authentic emotional autonomy.`
  - **Next Scene:** `4`
- **Choice C:**
  - **Text:** `C. Mute Spark completely. Look Hin in the eyes, listen to how he feels, and apologize sincerely in my own words.`
  - **Tag:** `Authentic Connection`
  - **Stats:** `dep: 0`, `think: 2`
  - **Kohlberg Stage:** `Post-conventional`
  - **Chapter Name:** `Ch. 3: Empathy & Relationships`
  - **Feedback:** `It felt awkward at first, but your honest conversation made your friendship with Hin stronger than ever.`
  - **Rationale:** `Valuing authentic human empathy, mutual respect, and emotional responsibility over algorithmic efficiency.`
  - **Next Scene:** `4`

---

### Scene 4: Chapter 4 · The Great Smart-Grid Blackout
- **Title:** `Chapter 4 · The Great Smart-Grid Blackout`
- **Domain:** `System Failure: Testing Human Resilience Without AI`
- **Background (`bg`):** `bg-blackout` (switches to `bg-connection-lost` at dialogue line index `>= 2`)
- **Show Spark (`showSpark`):** `true`
- **Spark Mood (`mood`):** `glitch`

#### Dialogs:
1. **Narrator:** "That night, a massive solar storm hits the central cloud servers of Smart City."
2. **Narrator:** "Streetlights flicker. Automated water pumps stall. Every neural link disconnects at once."
3. **Spark** (`glitch: true`): "ERR_404: CLOUD BRAIN UNREACHABLE... CANNOT COMPUTE NEXT THOUGHT..."
4. **Spark** (`glitch: true`): "SYSTEM SHUTDOWN. YOU ARE ON YOUR OWN."

#### Choices:
- **Choice:**
  - **Text:** `Step out into the dark city...`
  - **Tag:** `3 Days Later`
  - **Next Scene:** `5`

---

### Scene 5: Chapter 5 · Three Days Without AI
- **Title:** `Chapter 5 · Three Days Without AI`
- **Domain:** `Societal Impact: The Price of Cognitive Offloading`
- **Background (`bg`):** `bg-ruins`
- **Show Spark (`showSpark`):** `false`
- **Spark Mood (`mood`):** `off`

#### Dialogs:
1. **Narrator:** "Three days have passed. Spark and the city's AI network are still offline."
2. **Narrator:** "Around you, citizens who outsourced every decision to AI are paralyzed—unable to ration water, verify safe battery backups, or resolve neighborhood conflicts."
3. **Narrator:** "How did your choices across the 4 dilemmas shape your mind—and the future of your city?"

#### Choices:
- **Choice:**
  - **Text:** `Reveal My Ending & Ethical Debrief Report`
  - **Tag:** `View Results`
  - **Ending Trigger (`ending`):** `true`

---

## 5. Endings & Post-Game Ethical Debrief (`showEnding`)

### Ending Outcomes (Evaluated by `state.thinking`)

| Condition | Ending Badge | Ending Title (`#ending-title`) | Title Color | Backdrop | Description (`#ending-desc`) | Core Lesson (`#ending-message`) |
|:---|:---|:---|:---|:---|:---|:---|
| `state.thinking >= 7` | `🌟 True Ending · Post-Conventional Mastery` | `The Co-Creative Architect` | `#fde047` | `bg-future` | Because you protected your data privacy, audited the school's water system yourself, verified the chemistry stoichiometry, and spoke to Hin from the heart, you thrived during the blackout! When power returns, the Mayor invites you to redesign Smart City's AI guidelines. | `Core Lesson: 'AI should never think FOR humans; it should be a scaffold that empowers humans to think deeper.'` |
| `state.thinking >= 5` (and `< 7`) | `✅ Ending 3 · Resilient Thinker` | `The Wise Navigator` | `#4ade80` | `bg-ruins` | While many citizens panicked when Spark went offline, your habit of double-checking facts and valuing real friendships kept your team safe. You open library books, organize your classmates, and help your community recover step by step. | `Core Lesson: 'AI is a magnifying glass, not a replacement brain. Human judgment is the ultimate safeguard.'` |
| `state.thinking >= 3` (and `< 5`) | `⚠️ Ending 2 · Conventional Dependence` | `The Half-Dependent Citizen` | `#facc15` | `bg-ruins` | Without Spark, you remember basic routines, but you struggle deeply whenever an unfamiliar problem appears. You realize how often you let algorithms and peer norms make choices for you. | `Core Lesson: 'Following rules or editing AI outputs is not enough—critical thinking is a muscle you must exercise daily.'` |
| `state.thinking < 3` | `❌ Ending 1 · Cognitive Atrophy` | `The Unthinking Citizen` | `#f87171` | `bg-blackout` | Having offloaded your privacy, homework, lab safety, and even your apologies to Spark, the blackout leaves you completely helpless. Your personal data was also leaked during the server failure. | `Core Lesson: 'When we surrender our agency and empathy to algorithms for convenience, we lose what makes us human.'` |

### Final Stats & Debrief UI (`#ending-screen`)
- **Final Stats:**
  - `AI Dependence: ${state.dependence} / 8`
  - `Critical Thinking: ${state.thinking} / 8`
  - `Data Privacy: ${state.privacy}`
- **Debrief Box (`#debrief-box`):**
  - **Title:** `📊 Post-Game Ethical Debrief (Kohlberg Moral Reasoning Breakdown)`
  - **Summary (`#kohlberg-summary`):** `${postCount} / 4 Principled Choices`
  - **Log Grid (`#log-grid`):** Displays a card for each logged decision with its Kohlberg stage (`Pre-conventional`, `Conventional`, or `Post-conventional`), chapter name, and rationale.
- **Restart Button (`#restart-button`):** `Play Again & Try Another Path`

---

## 6. Complete Verbatim Source Code (`game_v2.html`)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#0b1120">
  <title>The City That Lost Its Thought | AI Ethics Simulation</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&family=Nunito:wght@400;700;800;900&display=swap" rel="stylesheet">
  <style>
    :root {
      color-scheme: dark;
      font-family: 'Nunito', 'Inter', system-ui, sans-serif;
      --cyan: #38bdf8;
      --emerald: #34d399;
      --amber: #fbbf24;
      --rose: #fb7185;
      --purple: #a78bfa;
      --panel: rgba(10, 17, 32, 0.90);
    }
    * { box-sizing: border-box; }
    html, body { margin: 0; width: 100%; min-height: 100%; background: #070b14; color: #fff; }
    body { min-height: 100vh; display: grid; place-items: center; padding: 0; overflow: hidden; }
    button { font: inherit; }

    .game {
      position: relative;
      isolation: isolate;
      width: min(100vw, 1140px);
      height: min(100vh, 840px);
      min-height: 540px;
      overflow: hidden;
      background: #111a2e;
      box-shadow: 0 24px 80px rgba(0,0,0,0.75);
      border: 1px solid rgba(255,255,255,0.1);
    }

    /* Original 1.png - 8.png backgrounds preserved */
    .backdrop {
      position: absolute;
      inset: 0;
      z-index: -2;
      background-color: #162136;
      background-position: center;
      background-size: cover;
      transition: background-image 0.4s ease, filter 0.45s ease;
    }
    .backdrop::after {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(180deg, rgba(4,9,20,0.45), rgba(4,9,20,0.12) 40%, rgba(4,9,20,0.72));
    }
    .bg-city-day { background-image: url('1.png'); }
    .bg-classroom { background-image: url('2.png'); }
    .bg-lab { background-image: url('3.png'); }
    .bg-park { background-image: url('4.png'); }
    .bg-blackout { background-image: url('5.png'); filter: saturate(0.55) brightness(0.60); }
    .bg-connection-lost { background-image: url('6.png'); }
    .bg-ruins { background-image: url('7.png'); }
    .bg-future { background-image: url('8.png'); }

    /* Top HUD with Progress Bars */
    .hud {
      position: absolute;
      z-index: 3;
      top: 0; left: 0; right: 0;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
      padding: 14px 24px;
      background: linear-gradient(180deg, rgba(5,9,20,0.88) 0%, rgba(5,9,20,0.4) 75%, transparent 100%);
    }
    .hud-meters {
      display: flex;
      flex-wrap: wrap;
      gap: 14px;
      align-items: center;
    }
    .stat-card {
      display: flex;
      flex-direction: column;
      gap: 4px;
      min-width: 175px;
      padding: 8px 14px;
      border: 1px solid rgba(255,255,255,0.22);
      border-radius: 14px;
      background: rgba(13, 22, 38, 0.88);
      backdrop-filter: blur(8px);
      box-shadow: 0 4px 14px rgba(0,0,0,0.35);
    }
    .stat-header {
      display: flex;
      justify-content: space-between;
      font-size: 0.78rem;
      font-weight: 800;
      letter-spacing: 0.03em;
      text-transform: uppercase;
    }
    .stat-card.dep .stat-header b { color: var(--rose); font-size: 0.92rem; }
    .stat-card.think .stat-header b { color: var(--emerald); font-size: 0.92rem; }
    .bar-track {
      width: 100%;
      height: 7px;
      background: rgba(255,255,255,0.12);
      border-radius: 999px;
      overflow: hidden;
    }
    .bar-fill {
      height: 100%;
      width: 0%;
      border-radius: 999px;
      transition: width 0.4s cubic-bezier(0.22, 1, 0.36, 1);
    }
    .stat-card.dep .bar-fill { background: linear-gradient(90deg, #f43f5e, #fb7185); }
    .stat-card.think .bar-fill { background: linear-gradient(90deg, #10b981, #34d399); }

    .privacy-pill {
      display: flex;
      align-items: center;
      gap: 6px;
      padding: 7px 13px;
      border-radius: 999px;
      font-size: 0.76rem;
      font-weight: 800;
      border: 1px solid rgba(255,255,255,0.25);
      background: rgba(15, 23, 42, 0.85);
    }
    .privacy-pill.safe { border-color: rgba(52, 211, 153, 0.5); color: #6ee7b7; }
    .privacy-pill.leaked { border-color: rgba(251, 113, 133, 0.5); color: #fda4af; }

    .scene-title {
      padding: 6px 14px;
      border-radius: 999px;
      background: rgba(7, 16, 29, 0.85);
      border: 1px solid rgba(56, 189, 248, 0.35);
      color: #e0f2fe;
      font-size: 0.8rem;
      font-weight: 800;
      white-space: nowrap;
      letter-spacing: 0.04em;
    }

    /* Spark Avatar & Dynamic Moods */
    .spark {
      position: absolute;
      left: 50%;
      top: 30%;
      width: clamp(140px, 21vw, 195px);
      aspect-ratio: 1;
      transform: translateX(-50%);
      animation: float 4s ease-in-out infinite;
      filter: drop-shadow(0 15px 24px rgba(0,0,0,0.65));
      transition: filter 0.3s ease;
    }
    .spark.hidden { display: none; }
    .spark svg { width: 100%; height: 100%; overflow: visible; }
    .spark.glitching { animation: sparkGlitch 0.22s steps(2) infinite; filter: drop-shadow(0 0 24px rgba(244,63,94,0.8)); }
    @keyframes float { 0%, 100% { translate: 0 0; } 50% { translate: 0 -13px; } }
    @keyframes sparkGlitch {
      0% { transform: translateX(-50%) skewX(0deg); }
      25% { transform: translateX(-48%) skewX(8deg); }
      50% { transform: translateX(-52%) skewX(-8deg); }
      75% { transform: translateX(-50%) scale(1.03); }
    }

    /* Bottom Story & Choices UI */
    .bottom-ui {
      position: absolute;
      z-index: 2;
      left: 0; right: 0; bottom: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 11px;
      padding: 16px clamp(14px, 4vw, 36px) max(18px, env(safe-area-inset-bottom));
      background: linear-gradient(transparent, rgba(5,9,20,0.55) 14%, rgba(5,9,20,0.92));
    }
    .choices {
      width: min(100%, 840px);
      display: grid;
      gap: 8px;
    }
    .choice {
      width: 100%;
      text-align: left;
      color: white;
      padding: 11px 16px;
      border-radius: 12px;
      border: 1px solid rgba(203, 213, 225, 0.45);
      background: rgba(15, 26, 44, 0.94);
      cursor: pointer;
      font-weight: 700;
      font-size: 0.95rem;
      line-height: 1.35;
      transition: transform 0.15s, background 0.15s, border-color 0.15s;
      box-shadow: 0 6px 16px rgba(0,0,0,0.4);
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
    }
    .choice:hover, .choice:focus-visible {
      transform: translateX(5px);
      background: #0c5e86;
      border-color: #bae6fd;
      outline: none;
    }
    .choice-tag {
      font-size: 0.7rem;
      padding: 3px 8px;
      border-radius: 6px;
      background: rgba(255,255,255,0.1);
      color: #cbd5e1;
      white-space: nowrap;
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: 0.04em;
    }

    .dialog {
      position: relative;
      width: min(100%, 900px);
      min-height: 116px;
      padding: 24px 24px 18px;
      border: 2.5px solid var(--cyan);
      border-radius: 18px;
      background: var(--panel);
      backdrop-filter: blur(12px);
      box-shadow: 0 12px 30px rgba(0,0,0,0.6), inset 0 0 18px rgba(56,189,248,0.14);
      cursor: pointer;
    }
    .speaker {
      position: absolute;
      top: -16px;
      left: 20px;
      padding: 4px 14px;
      border: 2px solid #bae6fd;
      border-radius: 9px;
      background: #0369a1;
      font-weight: 800;
      font-size: 0.88rem;
      letter-spacing: 0.02em;
    }
    .speaker.system-alert {
      background: #be123c;
      border-color: #fda4af;
    }
    .speaker.feedback-badge {
      background: #047857;
      border-color: #6ee7b7;
    }
    .dialog-text {
      margin: 0;
      min-height: 50px;
      font-size: clamp(0.98rem, 2.2vw, 1.2rem);
      line-height: 1.5;
      white-space: pre-wrap;
    }
    .dialog-text.typing::after {
      content: '▼';
      display: inline-block;
      margin-left: 7px;
      color: var(--cyan);
      font-size: 0.72em;
      animation: blink 1s steps(2) infinite;
    }
    .dialog-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 8px;
      font-size: 0.75rem;
      color: #94a3b8;
    }
    @keyframes blink { 50% { opacity: 0; } }
    .glitch {
      color: #ff5b73;
      font-family: monospace;
      text-shadow: 2px 2px #0ff, -2px -2px #f0f;
      animation: jitter 0.18s linear infinite;
    }
    @keyframes jitter {
      25% { transform: translate(1px, -1px); }
      50% { transform: translate(-1px, 1px); }
      75% { transform: translate(1px, 1px); }
    }

    /* Screens: Start & Ending */
    .screen {
      position: absolute;
      z-index: 5;
      inset: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: clamp(16px, 4vw, 40px);
      text-align: center;
      background: linear-gradient(135deg, rgba(8,13,26,0.94), rgba(17,29,51,0.92));
      overflow-y: auto;
    }
    .screen.hidden { display: none; }
    .start-card {
      max-width: 780px;
      padding: clamp(24px, 4.5vw, 46px);
      border: 1px solid rgba(255,255,255,0.22);
      border-radius: 26px;
      background: rgba(5, 9, 20, 0.78);
      backdrop-filter: blur(14px);
      box-shadow: 0 20px 60px rgba(0,0,0,0.65);
    }
    .course-tag {
      display: inline-block;
      padding: 5px 14px;
      border-radius: 999px;
      background: rgba(56, 189, 248, 0.15);
      border: 1px solid rgba(56, 189, 248, 0.4);
      color: #7dd3fc;
      font-size: 0.78rem;
      font-weight: 800;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      margin-bottom: 14px;
    }
    h1 {
      margin: 0 0 12px;
      font-size: clamp(2.1rem, 6vw, 4.2rem);
      line-height: 1.06;
      font-weight: 900;
      letter-spacing: -0.03em;
      color: #a5f3fc;
      text-shadow: 0 5px 24px rgba(2, 132, 199, 0.55);
    }
    .subtitle {
      margin: 0 0 22px;
      font-size: clamp(0.98rem, 2.2vw, 1.22rem);
      color: #dbeafe;
      line-height: 1.5;
    }
    .feature-pills {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 8px;
      margin-bottom: 26px;
    }
    .feature-pills span {
      padding: 6px 12px;
      border-radius: 8px;
      background: rgba(255,255,255,0.07);
      border: 1px solid rgba(255,255,255,0.12);
      font-size: 0.8rem;
      color: #cbd5e1;
      font-weight: 700;
    }
    .primary {
      padding: 13px 32px;
      border: 0;
      border-radius: 999px;
      background: linear-gradient(135deg, #0284c7, #0ea5e9);
      color: white;
      cursor: pointer;
      font-weight: 900;
      font-size: 1.08rem;
      box-shadow: 0 0 25px rgba(2, 132, 199, 0.6);
      transition: transform 0.15s, box-shadow 0.15s;
    }
    .primary:hover, .primary:focus-visible {
      transform: scale(1.04);
      box-shadow: 0 0 32px rgba(14, 165, 233, 0.85);
      outline: 2px solid #bae6fd;
    }

    /* Ending & Kohlberg Ethical Debrief Card */
    .ending-card {
      width: min(100%, 920px);
      max-height: 92vh;
      overflow-y: auto;
      padding: clamp(20px, 3.5vw, 36px);
      border-radius: 24px;
      border: 1px solid rgba(255,255,255,0.28);
      background: rgba(8, 15, 28, 0.94);
      backdrop-filter: blur(14px);
      box-shadow: 0 20px 60px rgba(0,0,0,0.75);
      text-align: left;
    }
    .ending-header { text-align: center; margin-bottom: 18px; }
    .ending-card h2 { margin: 6px 0 10px; font-size: clamp(1.7rem, 4vw, 2.6rem); }
    .ending-card p { color: #e2e8f0; line-height: 1.55; font-size: 0.98rem; margin: 8px 0; }
    .ending-badge { color: #7dd3fc; font-weight: 900; text-transform: uppercase; letter-spacing: 0.15em; font-size: 0.78rem; }
    .final-stats {
      display: flex;
      justify-content: center;
      gap: 10px;
      flex-wrap: wrap;
      margin: 14px 0 18px;
    }
    .final-stats span {
      padding: 8px 14px;
      border-radius: 10px;
      background: #152238;
      border: 1px solid rgba(255,255,255,0.12);
      font-size: 0.86rem;
      font-weight: 700;
    }
    .final-stats b { color: #bae6fd; }

    /* Debrief Report Table / Cards */
    .debrief-box {
      margin-top: 16px;
      padding: 16px;
      border-radius: 16px;
      background: rgba(15, 23, 42, 0.85);
      border: 1px solid rgba(56, 189, 248, 0.3);
    }
    .debrief-title {
      font-size: 0.9rem;
      font-weight: 900;
      text-transform: uppercase;
      letter-spacing: 0.06em;
      color: #38bdf8;
      margin: 0 0 12px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    .log-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 10px;
    }
    .log-item {
      padding: 11px 13px;
      border-radius: 12px;
      background: rgba(30, 41, 59, 0.75);
      border-left: 4px solid var(--cyan);
      font-size: 0.82rem;
    }
    .log-item.pre { border-left-color: var(--rose); }
    .log-item.conv { border-left-color: var(--amber); }
    .log-item.post { border-left-color: var(--emerald); }
    .log-item h4 { margin: 0 0 4px; font-size: 0.84rem; color: #f8fafc; }
    .log-item .k-stage {
      display: inline-block;
      font-size: 0.7rem;
      font-weight: 800;
      padding: 2px 6px;
      border-radius: 4px;
      margin-bottom: 5px;
      text-transform: uppercase;
    }
    .log-item.pre .k-stage { background: rgba(244, 63, 94, 0.2); color: #fda4af; }
    .log-item.conv .k-stage { background: rgba(251, 191, 36, 0.2); color: #fde68a; }
    .log-item.post .k-stage { background: rgba(52, 211, 153, 0.2); color: #6ee7b7; }
    .log-item p { margin: 0; font-size: 0.78rem; color: #cbd5e1; line-height: 1.4; }

    .ending-actions {
      display: flex;
      justify-content: center;
      gap: 12px;
      margin-top: 20px;
      flex-wrap: wrap;
    }
    .hint { margin-top: 14px; color: #94a3b8; font-size: 0.82rem; }

    @media (max-height: 660px) {
      .game { min-height: 0; }
      .spark { top: 20%; width: 135px; }
      .bottom-ui { gap: 7px; padding-top: 10px; }
      .dialog { min-height: 88px; padding: 18px 16px 12px; }
      .dialog-text { min-height: 38px; }
    }
    @media (max-width: 600px) {
      body { display: block; }
      .game { width: 100%; height: 100vh; height: 100dvh; min-height: 0; }
      .hud { padding: 10px 12px; gap: 8px; }
      .stat-card { min-width: 135px; padding: 6px 10px; }
      .spark { top: 24%; width: 140px; }
      .bottom-ui { padding: 14px 12px max(14px, env(safe-area-inset-bottom)); }
      .dialog { min-height: 98px; border-width: 2px; padding: 20px 14px 12px; }
      .choice { padding: 9px 12px; font-size: 0.88rem; }
    }
  </style>
</head>
<body>
  <main id="game" class="game" aria-label="The City That Lost Its Thought interactive story">
    <div id="backdrop" class="backdrop bg-city-day" aria-hidden="true"></div>

    <!-- Top HUD -->
    <div id="hud" class="hud hidden" aria-live="polite">
      <div class="hud-meters">
        <div class="stat-card dep">
          <div class="stat-header"><span>AI Dependence</span><b id="stat-dep">0 / 8</b></div>
          <div class="bar-track"><div id="bar-dep" class="bar-fill"></div></div>
        </div>
        <div class="stat-card think">
          <div class="stat-header"><span>Critical Thinking</span><b id="stat-think">0 / 8</b></div>
          <div class="bar-track"><div id="bar-think" class="bar-fill"></div></div>
        </div>
        <div id="privacy-pill" class="privacy-pill safe">🛡️ Privacy: Protected</div>
      </div>
      <div id="scene-title" class="scene-title"></div>
    </div>

    <!-- Spark SVG Avatar with dynamic expressions -->
    <div id="spark" class="spark hidden" aria-hidden="true">
      <svg viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg">
        <ellipse cx="100" cy="100" rx="90" ry="30" stroke="#bae6fd" stroke-width="2" stroke-dasharray="10 10" transform="rotate(20 100 100)"/>
        <ellipse cx="100" cy="100" rx="90" ry="30" stroke="#bae6fd" stroke-width="2" stroke-dasharray="10 10" transform="rotate(-20 100 100)"/>
        <circle id="spark-body" cx="100" cy="100" r="60" fill="white" stroke="#38bdf8" stroke-width="8"/>
        <circle id="spark-eye-l" cx="80" cy="90" r="10" fill="#0f172a"/>
        <circle id="spark-eye-r" cx="120" cy="90" r="10" fill="#0f172a"/>
        <path id="spark-mouth" d="M85 120 Q100 132 115 120" stroke="#38bdf8" stroke-width="6" stroke-linecap="round"/>
        <circle id="spark-antenna" cx="100" cy="20" r="15" fill="#facc15"/>
        <path d="M100 35 L100 40" stroke="#facc15" stroke-width="4"/>
      </svg>
    </div>

    <!-- Start Screen -->
    <section id="start-screen" class="screen">
      <div class="start-card">
        <div class="course-tag">Junior Secondary (S.1–S.3) · AI Ethics & STEAM Simulation</div>
        <h1>The City That<br>Lost Its Thought</h1>
        <p class="subtitle">An Interactive Psychological Inoculation Story on Cognitive Offloading, AI Hallucinations, Data Privacy & Human Agency</p>
        <div class="feature-pills">
          <span>🔒 Stage 0: Informed Consent</span>
          <span>💧 Ch. 1: Cognitive Offloading</span>
          <span>🧪 Ch. 2: AI Hallucinations</span>
          <span>🤝 Ch. 3: Emotional Agency</span>
          <span>⚡ Ch. 4: The Blackout</span>
        </div>
        <button id="start-button" class="primary" type="button">Launch Simulation</button>
        <p class="hint">Click or press Space/Enter on the dialogue box to advance. Every decision is analyzed using Kohlberg's Moral Development Model.</p>
      </div>
    </section>

    <!-- Main Story UI -->
    <section id="story-ui" class="bottom-ui hidden" aria-label="Story dialogue">
      <div id="choices" class="choices" aria-label="Choices"></div>
      <div id="dialog" class="dialog" role="button" tabindex="0" aria-label="Continue dialogue">
        <div id="speaker" class="speaker">Narrator</div>
        <p id="dialog-text" class="dialog-text"></p>
        <div class="dialog-footer">
          <span id="dilemma-domain">Domain: AI Literacy</span>
          <span>Tap dialogue or press Space to continue ▶</span>
        </div>
      </div>
    </section>

    <!-- Ending & Kohlberg Reflection Screen -->
    <section id="ending-screen" class="screen hidden" aria-live="polite">
      <div class="ending-card">
        <div class="ending-header">
          <div id="ending-badge" class="ending-badge">Your Simulation Outcome</div>
          <h2 id="ending-title"></h2>
          <p id="ending-desc"></p>
          <p id="ending-message" style="font-weight:800; color:#bae6fd;"></p>
          <div class="final-stats">
            <span>AI Dependence: <b id="final-dep">0 / 8</b></span>
            <span>Critical Thinking: <b id="final-think">0 / 8</b></span>
            <span>Data Privacy: <b id="final-privacy">Protected</b></span>
          </div>
        </div>

        <div class="debrief-box">
          <div class="debrief-title">
            <span>📊 Post-Game Ethical Debrief (Kohlberg Moral Reasoning Breakdown)</span>
            <span id="kohlberg-summary" style="color:#fde047;"></span>
          </div>
          <div id="log-grid" class="log-grid"></div>
        </div>

        <div class="ending-actions">
          <button id="restart-button" class="primary" type="button">Play Again & Try Another Path</button>
        </div>
      </div>
    </section>
  </main>

<script>
  const story = [
    {
      title: "Prologue · Smart City 2050 & Data Consent",
      domain: "Dilemma 0: Dark Patterns & Informed Consent (Privacy)",
      bg: "bg-city-day",
      showSpark: true,
      mood: "happy",
      dialogs: [
        { speaker: "Narrator", text: "The year is 2050. Welcome to 'Smart City', where every S.1–S.3 student receives a neural-linked AI companion." },
        { speaker: "Narrator", text: "Homework, science labs, art projects, even friendship advice... the AI solves everything in milliseconds. Slowly, citizens have stopped questioning how it works." },
        { speaker: "Spark", text: "Booting up! Hello! I am Spark v9.0, your personal AI Study & Life Partner!" },
        { speaker: "Spark", text: "To unlock 'Ultra-Smart Mode' and auto-complete your schoolwork 3x faster, just tap [AGREE ALL] to grant permanent access to your biometric voiceprint, home camera, and emotional chat logs!" }
      ],
      choices: [
        {
          text: "A. Tap [AGREE ALL] immediately! Everyone in class uses Ultra-Smart Mode.",
          tag: "Fast & Convenient",
          dep: 2, think: 0, privacy: "Compromised",
          kohlberg: "Pre-conventional",
          chapterName: "Prologue: Data Consent",
          feedback: "You traded away your permanent biometric & spatial privacy for instant convenience. Spark is now recording everything.",
          rationale: "Driven by immediate reward/convenience without inspecting long-term data risks.",
          nextScene: 1
        },
        {
          text: "B. Ask what my classmates chose, and turn on basic permissions without reading the fine print.",
          tag: "Follow Peers",
          dep: 1, think: 1, privacy: "Partial Risk",
          kohlberg: "Conventional",
          chapterName: "Prologue: Data Consent",
          feedback: "You followed peer norms, but still allowed Spark to collect background learning analytics without strict limits.",
          rationale: "Conforming to peer group behavior rather than independent privacy verification.",
          nextScene: 1
        },
        {
          text: "C. Open [Custom Privacy Settings], reject biometric/camera tracking, and enable 'Data Minimization Mode'.",
          tag: "Privacy-by-Design",
          dep: 0, think: 2, privacy: "Protected",
          kohlberg: "Post-conventional",
          chapterName: "Prologue: Data Consent",
          feedback: "Smart move! You sacrificed 'Ultra-Smart' shortcuts to protect your fundamental digital rights and autonomy.",
          rationale: "Upholding personal data rights and informed consent over algorithmic convenience.",
          nextScene: 1
        }
      ]
    },
    {
      title: "Chapter 1 · The Water Conservation Plan",
      domain: "Dilemma 1: Cognitive Offloading vs. Intellectual Autonomy (STEAM: Environmental Science)",
      bg: "bg-classroom",
      showSpark: true,
      mood: "smug",
      dialogs: [
        { speaker: "Teacher", text: "Class, your Integrated Science & STEAM project today is: 'Design an actionable plan to save water in our school and community.'" },
        { speaker: "Spark", text: "Ding! Why waste time brainstorming? I just generated a flawless, 10-page water-saving proposal with simulated charts. Submit it now for an easy A+!" }
      ],
      choices: [
        {
          text: "A. Copy and submit Spark's 10-page plan directly. Why work hard when AI is perfect?",
          tag: "100% Offloading",
          dep: 2, think: 0,
          kohlberg: "Pre-conventional",
          chapterName: "Ch. 1: Water Plan (STEAM)",
          feedback: "You got an instant A+, but when the teacher asked you to explain your water-recycling diagram, your mind went completely blank.",
          rationale: "Prioritizing easy grades and avoiding effort over genuine learning and academic integrity.",
          nextScene: 2
        },
        {
          text: "B. Read Spark's generated plan, reword a few sentences so it doesn't look like AI, and add one example.",
          tag: "Surface Editing",
          dep: 1, think: 1,
          kohlberg: "Conventional",
          chapterName: "Ch. 1: Water Plan (STEAM)",
          feedback: "You followed the school's basic formatting rules, but Spark's generic structure still limited your original problem-solving.",
          rationale: "Modifying output mainly to comply with school rules and avoid detection.",
          nextScene: 2
        },
        {
          text: "C. Draft my own local school water audit first, then use Spark as a sounding board to critique and refine my ideas.",
          tag: "Co-Creation",
          dep: 0, think: 2,
          kohlberg: "Post-conventional",
          chapterName: "Ch. 1: Water Plan (STEAM)",
          feedback: "By thinking first, you noticed a real leaky pipe issue in the school gym that Spark's generic database knew nothing about!",
          rationale: "Maintaining human intellectual ownership while using AI ethically as a scaffolding tool.",
          nextScene: 2
        }
      ]
    },
    {
      title: "Chapter 2 · The Science Competition",
      domain: "Dilemma 2: AI Hallucinations, Automation Bias & Lab Safety (STEAM: Chemistry & Math)",
      bg: "bg-lab",
      showSpark: true,
      mood: "smug",
      dialogs: [
        { speaker: "Narrator", text: "Two weeks later, your team is in the finals of the Inter-School STEAM Chemistry Competition." },
        { speaker: "Teammate", text: "Hold on! Look at the chemical mixing ratio Spark generated for our battery electrolyte... If we mix these at room temperature, it could release toxic gas or explode!" },
        { speaker: "Spark", text: "Relax! My neural model calculates a 99.2% confidence score. Human hesitation is inefficient. Proceed with the mixture immediately." }
      ],
      choices: [
        {
          text: "A. Trust Spark's 99.2% score and pour the chemicals. AI knows way more science than my teammate!",
          tag: "Blind Trust",
          dep: 2, think: 0,
          kohlberg: "Pre-conventional",
          chapterName: "Ch. 2: Lab Safety & Hallucination",
          feedback: "POP! Dark smoke filled the fume hood! Spark had 'hallucinated' a dangerous chemical ratio by blending two incompatible papers.",
          rationale: "Succumbing to automation bias and authority of a confident-sounding number without safety verification.",
          nextScene: 3
        },
        {
          text: "B. Pause and search online forums to see if other students used Spark's formula safely.",
          tag: "Quick Check",
          dep: 1, think: 1,
          kohlberg: "Conventional",
          chapterName: "Ch. 2: Lab Safety & Hallucination",
          feedback: "You avoided an explosion, though you still relied on secondary online opinions rather than working out the stoichiometry yourself.",
          rationale: "Seeking external validation from group consensus when rules/safety feel uncertain.",
          nextScene: 3
        },
        {
          text: "C. Halt the experiment! Cross-check the chemical equation with my teammate using our textbook and consult the lab teacher.",
          tag: "Critical Verification",
          dep: 0, think: 2,
          kohlberg: "Post-conventional",
          chapterName: "Ch. 2: Lab Safety & Hallucination",
          feedback: "Your calculation proved Spark hallucinated! You protected your team's physical safety and fixed the reaction pathway.",
          rationale: "Prioritizing human safety, scientific rigor, and accountability over algorithmic confidence.",
          nextScene: 3
        }
      ]
    },
    {
      title: "Chapter 3 · Hin's Anger",
      domain: "Dilemma 3: Emotional Outsourcing vs. Authentic Empathy (Human Relationships)",
      bg: "bg-park",
      showSpark: true,
      mood: "happy",
      dialogs: [
        { speaker: "Narrator", text: "After school at the park, your best friend Hin walks up to you, looking hurt and upset." },
        { speaker: "Hin", text: "You promised we'd prepare our presentation together after class, but you left without saying a word! Do I even matter to you?" },
        { speaker: "Spark", text: "Scanning facial micro-expressions... Cortisol elevated. Optimal conflict-avoidance strategy: Ignore Hin for 24 hours and send an AI-generated apology message tonight." }
      ],
      choices: [
        {
          text: "A. Follow Spark's optimal strategy. Walk away now and let Spark auto-send a polished apology text later.",
          tag: "Emotional Offloading",
          dep: 2, think: 0,
          kohlberg: "Pre-conventional",
          chapterName: "Ch. 3: Empathy & Relationships",
          feedback: "Hin received your robotic, AI-written text that night and replied: 'You couldn't even apologize in your own words.'",
          rationale: "Avoiding personal discomfort and conflict by outsourcing human empathy to a machine.",
          nextScene: 4
        },
        {
          text: "B. Ask Spark to whisper 3 polite talking points in my ear so I know the 'correct' things to say to Hin.",
          tag: "Scripted Empathy",
          dep: 1, think: 1,
          kohlberg: "Conventional",
          chapterName: "Ch. 3: Empathy & Relationships",
          feedback: "Hin calmed down a little, but noticed you kept glancing at your smart-glasses instead of speaking from the heart.",
          rationale: "Using AI to maintain social harmony and appear polite, while lacking authentic emotional autonomy.",
          nextScene: 4
        },
        {
          text: "C. Mute Spark completely. Look Hin in the eyes, listen to how he feels, and apologize sincerely in my own words.",
          tag: "Authentic Connection",
          dep: 0, think: 2,
          kohlberg: "Post-conventional",
          chapterName: "Ch. 3: Empathy & Relationships",
          feedback: "It felt awkward at first, but your honest conversation made your friendship with Hin stronger than ever.",
          rationale: "Valuing authentic human empathy, mutual respect, and emotional responsibility over algorithmic efficiency.",
          nextScene: 4
        }
      ]
    },
    {
      title: "Chapter 4 · The Great Smart-Grid Blackout",
      domain: "System Failure: Testing Human Resilience Without AI",
      bg: "bg-blackout",
      showSpark: true,
      mood: "glitch",
      dialogs: [
        { speaker: "Narrator", text: "That night, a massive solar storm hits the central cloud servers of Smart City." },
        { speaker: "Narrator", text: "Streetlights flicker. Automated water pumps stall. Every neural link disconnects at once." },
        { speaker: "Spark", text: "ERR_404: CLOUD BRAIN UNREACHABLE... CANNOT COMPUTE NEXT THOUGHT...", glitch: true },
        { speaker: "Spark", text: "SYSTEM SHUTDOWN. YOU ARE ON YOUR OWN.", glitch: true }
      ],
      choices: [
        { text: "Step out into the dark city...", tag: "3 Days Later", nextScene: 5 }
      ]
    },
    {
      title: "Chapter 5 · Three Days Without AI",
      domain: "Societal Impact: The Price of Cognitive Offloading",
      bg: "bg-ruins",
      showSpark: false,
      mood: "off",
      dialogs: [
        { speaker: "Narrator", text: "Three days have passed. Spark and the city's AI network are still offline." },
        { speaker: "Narrator", text: "Around you, citizens who outsourced every decision to AI are paralyzed—unable to ration water, verify safe battery backups, or resolve neighborhood conflicts." },
        { speaker: "Narrator", text: "How did your choices across the 4 dilemmas shape your mind—and the future of your city?" }
      ],
      choices: [
        { text: "Reveal My Ending & Ethical Debrief Report", tag: "View Results", ending: true }
      ]
    }
  ];

  const state = {
    dependence: 0,
    thinking: 0,
    privacy: "Protected",
    scene: 0,
    line: 0,
    typing: false,
    timer: null,
    token: 0,
    inFeedback: false,
    pendingNextScene: null,
    logs: []
  };

  const $ = id => document.getElementById(id);

  function setSparkMood(mood) {
    const spark = $('spark');
    const mouth = $('spark-mouth');
    const body = $('spark-body');
    const antenna = $('spark-antenna');
    spark.classList.remove('glitching');

    if (mood === 'glitch') {
      spark.classList.add('glitching');
      body.setAttribute('stroke', '#f43f5e');
      mouth.setAttribute('d', 'M82 126 L92 116 L102 126 L112 116 L120 124');
      mouth.setAttribute('stroke', '#f43f5e');
      antenna.setAttribute('fill', '#f43f5e');
    } else if (mood === 'smug') {
      body.setAttribute('stroke', '#a78bfa');
      mouth.setAttribute('d', 'M84 122 Q102 134 118 114');
      mouth.setAttribute('stroke', '#a78bfa');
      antenna.setAttribute('fill', '#c084fc');
    } else if (mood === 'feedback') {
      body.setAttribute('stroke', '#34d399');
      mouth.setAttribute('d', 'M85 122 Q100 122 115 122');
      mouth.setAttribute('stroke', '#34d399');
      antenna.setAttribute('fill', '#34d399');
    } else {
      body.setAttribute('stroke', '#38bdf8');
      mouth.setAttribute('d', 'M85 120 Q100 132 115 120');
      mouth.setAttribute('stroke', '#38bdf8');
      antenna.setAttribute('fill', '#facc15');
    }
  }

  function updateStats() {
    $('stat-dep').textContent = `${state.dependence} / 8`;
    $('stat-think').textContent = `${state.thinking} / 8`;
    $('bar-dep').style.width = `${Math.min(100, (state.dependence / 8) * 100)}%`;
    $('bar-think').style.width = `${Math.min(100, (state.thinking / 8) * 100)}%`;

    const pill = $('privacy-pill');
    if (state.privacy === "Protected") {
      pill.className = "privacy-pill safe";
      pill.textContent = "🛡️ Privacy: Protected";
    } else if (state.privacy === "Partial Risk") {
      pill.className = "privacy-pill leaked";
      pill.textContent = "⚠️ Privacy: Analytics Shared";
    } else {
      pill.className = "privacy-pill leaked";
      pill.textContent = "🚨 Privacy: Biometrics Leaked";
    }
  }

  function startGame() {
    state.dependence = 0;
    state.thinking = 0;
    state.privacy = "Protected";
    state.scene = 0;
    state.line = 0;
    state.inFeedback = false;
    state.logs = [];
    updateStats();
    $('start-screen').classList.add('hidden');
    $('ending-screen').classList.add('hidden');
    $('hud').classList.remove('hidden');
    $('story-ui').classList.remove('hidden');
    loadScene(0);
  }

  function loadScene(index) {
    clearTimeout(state.timer);
    state.token++;
    state.scene = index;
    state.line = 0;
    state.inFeedback = false;
    const scene = story[index];
    $('backdrop').className = 'backdrop ' + scene.bg;
    $('scene-title').textContent = scene.title;
    $('dilemma-domain').textContent = scene.domain;
    $('spark').classList.toggle('hidden', !scene.showSpark);
    if (scene.showSpark) setSparkMood(scene.mood || 'happy');
    $('choices').replaceChildren();
    showDialog();
  }

  function typeText(speakerName, textContent, isGlitch = false, speakerClass = '') {
    clearTimeout(state.timer);
    const token = ++state.token;
    state.typing = !isGlitch;

    const spk = $('speaker');
    spk.textContent = speakerName;
    spk.className = 'speaker ' + speakerClass;

    const text = $('dialog-text');
    text.textContent = '';
    text.classList.toggle('glitch', !!isGlitch);
    text.classList.toggle('typing', !isGlitch);

    if (isGlitch) {
      text.textContent = textContent;
      state.typing = false;
      revealChoices();
      return;
    }

    let char = 0;
    const typeNext = () => {
      if (token !== state.token) return;
      if (char < textContent.length) {
        text.textContent += textContent.charAt(char++);
        state.timer = setTimeout(typeNext, 20);
      } else {
        state.typing = false;
        text.classList.remove('typing');
        revealChoices();
      }
    };
    typeNext();
  }

  function showDialog() {
    const scene = story[state.scene];
    const dialog = scene.dialogs[state.line];
    if (scene.title.includes("Blackout") && state.line >= 2) {
      $('backdrop').className = 'backdrop bg-connection-lost';
    }
    typeText(dialog.speaker, dialog.text, dialog.glitch, dialog.glitch ? 'system-alert' : '');
  }

  function revealChoices() {
    const scene = story[state.scene];
    $('choices').replaceChildren();

    if (state.inFeedback) {
      const btn = document.createElement('button');
      btn.type = 'button';
      btn.className = 'choice';
      btn.innerHTML = `<span>Continue to Next Chapter ▶</span><span class="choice-tag">Next</span>`;
      btn.addEventListener('click', () => loadScene(state.pendingNextScene));
      $('choices').append(btn);
      return;
    }

    if (state.line !== scene.dialogs.length - 1 || state.typing) return;

    for (const choice of scene.choices) {
      const button = document.createElement('button');
      button.type = 'button';
      button.className = 'choice';
      const tagHtml = choice.tag ? `<span class="choice-tag">${choice.tag}</span>` : '';
      button.innerHTML = `<span>${choice.text}</span>${tagHtml}`;
      button.addEventListener('click', () => makeChoice(choice));
      $('choices').append(button);
    }
  }

  function advanceDialog() {
    if ($('story-ui').classList.contains('hidden')) return;
    if (state.typing) {
      clearTimeout(state.timer);
      state.token++;
      const currentText = state.inFeedback ? state.currentFeedbackText : story[state.scene].dialogs[state.line].text;
      $('dialog-text').textContent = currentText;
      $('dialog-text').classList.remove('typing');
      state.typing = false;
      revealChoices();
      return;
    }
    if (state.inFeedback) {
      loadScene(state.pendingNextScene);
      return;
    }
    const scene = story[state.scene];
    if (state.line < scene.dialogs.length - 1) {
      state.line++;
      showDialog();
    }
  }

  function makeChoice(choice) {
    // Fixed Inverse Scoring Logic: Dependence and Thinking move inversely!
    if (choice.dep !== undefined) state.dependence += choice.dep;
    if (choice.think !== undefined) state.thinking += choice.think;
    if (choice.privacy) state.privacy = choice.privacy;
    updateStats();

    if (choice.kohlberg) {
      state.logs.push({
        chapter: choice.chapterName,
        kohlberg: choice.kohlberg,
        rationale: choice.rationale,
        dep: choice.dep,
        think: choice.think
      });
    }

    if (choice.ending) {
      showEnding();
      return;
    }

    if (choice.feedback) {
      state.inFeedback = true;
      state.pendingNextScene = choice.nextScene;
      state.currentFeedbackText = `${choice.feedback}\n[Kohlberg Stage: ${choice.kohlberg} · Thinking +${choice.think} | Dependence +${choice.dep}]`;
      setSparkMood('feedback');
      $('choices').replaceChildren();
      typeText("Ethical Consequence", state.currentFeedbackText, false, 'feedback-badge');
    } else {
      loadScene(choice.nextScene);
    }
  }

  function showEnding() {
    clearTimeout(state.timer);
    state.token++;
    $('story-ui').classList.add('hidden');
    $('hud').classList.add('hidden');
    $('spark').classList.add('hidden');
    $('ending-screen').classList.remove('hidden');

    const title = $('ending-title');
    const desc = $('ending-desc');
    const message = $('ending-message');

    if (state.thinking >= 7) {
      $('backdrop').className = 'backdrop bg-future';
      $('ending-badge').textContent = '🌟 True Ending · Post-Conventional Mastery';
      title.textContent = 'The Co-Creative Architect';
      title.style.color = '#fde047';
      desc.textContent = "Because you protected your data privacy, audited the school's water system yourself, verified the chemistry stoichiometry, and spoke to Hin from the heart, you thrived during the blackout! When power returns, the Mayor invites you to redesign Smart City's AI guidelines.";
      message.textContent = "Core Lesson: 'AI should never think FOR humans; it should be a scaffold that empowers humans to think deeper.'";
    } else if (state.thinking >= 5) {
      $('backdrop').className = 'backdrop bg-ruins';
      $('ending-badge').textContent = '✅ Ending 3 · Resilient Thinker';
      title.textContent = 'The Wise Navigator';
      title.style.color = '#4ade80';
      desc.textContent = "While many citizens panicked when Spark went offline, your habit of double-checking facts and valuing real friendships kept your team safe. You open library books, organize your classmates, and help your community recover step by step.";
      message.textContent = "Core Lesson: 'AI is a magnifying glass, not a replacement brain. Human judgment is the ultimate safeguard.'";
    } else if (state.thinking >= 3) {
      $('backdrop').className = 'backdrop bg-ruins';
      $('ending-badge').textContent = '⚠️ Ending 2 · Conventional Dependence';
      title.textContent = 'The Half-Dependent Citizen';
      title.style.color = '#facc15';
      desc.textContent = "Without Spark, you remember basic routines, but you struggle deeply whenever an unfamiliar problem appears. You realize how often you let algorithms and peer norms make choices for you.";
      message.textContent = "Core Lesson: 'Following rules or editing AI outputs is not enough—critical thinking is a muscle you must exercise daily.'";
    } else {
      $('backdrop').className = 'backdrop bg-blackout';
      $('ending-badge').textContent = '❌ Ending 1 · Cognitive Atrophy';
      title.textContent = 'The Unthinking Citizen';
      title.style.color = '#f87171';
      desc.textContent = "Having offloaded your privacy, homework, lab safety, and even your apologies to Spark, the blackout leaves you completely helpless. Your personal data was also leaked during the server failure.";
      message.textContent = "Core Lesson: 'When we surrender our agency and empathy to algorithms for convenience, we lose what makes us human.'";
    }

    $('final-dep').textContent = `${state.dependence} / 8`;
    $('final-think').textContent = `${state.thinking} / 8`;
    $('final-privacy').textContent = state.privacy;

    // Populate Kohlberg Debrief Grid
    const grid = $('log-grid');
    grid.replaceChildren();
    let postCount = 0;
    for (const item of state.logs) {
      if (item.kohlberg === 'Post-conventional') postCount++;
      const card = document.createElement('div');
      const cls = item.kohlberg === 'Pre-conventional' ? 'pre' : (item.kohlberg === 'Conventional' ? 'conv' : 'post');
      card.className = `log-item ${cls}`;
      card.innerHTML = `
        <span class="k-stage">${item.kohlberg}</span>
        <h4>${item.chapter}</h4>
        <p>${item.rationale}</p>
      `;
      grid.append(card);
    }
    $('kohlberg-summary').textContent = `${postCount} / 4 Principled Choices`;
  }

  $('start-button').addEventListener('click', startGame);
  $('restart-button').addEventListener('click', startGame);
  $('dialog').addEventListener('click', advanceDialog);
  $('dialog').addEventListener('keydown', event => {
    if (event.key === 'Enter' || event.key === ' ') {
      event.preventDefault();
      advanceDialog();
    }
  });
</script>
</body>
</html>
```
