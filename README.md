# natural-thai

Skill สำหรับ AI Coding Assistant และ Agent เพื่อให้เขียนและตอบเป็นภาษาไทยที่เป็นธรรมชาติ อ่านเข้าใจง่าย สื่อสารเหมือนคนทำงานจริง ๆ คุยกัน โดยไม่ใช้สำนวนแข็งทื่อหรือโครงสร้างประโยคแปลตรงตัวแบบ AI

โปรเจกต์นี้สร้างขึ้นตามมาตรฐาน **Agent Skills Open Standard** (agentskills.io) เป็น Standalone Skill สากลที่ใช้งานได้กับ Claude Code, GitHub Copilot, Cursor, Windsurf, Cline, Google Antigravity รวมถึง LLMs ทั่วไปอย่าง ChatGPT, Claude.ai และ Gemini *(อยู่ระหว่างการพัฒนา)*

---

## จุดเด่น

- **ภาษาเป็นธรรมชาติ :** ตัดโครงสร้างประโยคแปลอังกฤษตรงตัว ประโยคกรรมที่ฝืนธรรมชาติ ("ถูก...") และคำเชื่อมทางการซ้ำซาก
- **ไม่เพี้ยนความหมาย (Zero Semantic Drift) :** ล็อกหมุดความหมาย 6 ประการ เพื่อคงเงื่อนไข ข้อยกเว้น ขอบเขต และภาระหน้าที่ไว้ครบ 100%
- **ปรับระดับภาษาตามบริบท (Adaptive Tone) :** ปรับระดับภาษา 5 ระดับให้เข้ากับผู้รับสาร ทั้งการคุยกับหัวหน้า ลูกค้า เพื่อนร่วมงาน หรือคนทั่วไป
- **คำทับศัพท์และการเว้นวรรคที่ถูกต้อง :** ยึดตามหลักเกณฑ์ราชบัณฑิตยสภา (เช่น เช็ก, อัปเดต, โปรเจกต์, เซิร์ฟเวอร์, ลิงก์) พร้อมเว้นวรรคระหว่างภาษาไทย ภาษาอังกฤษ ตัวเลข และไม้ยมก (ๆ) ให้อ่านสบายตา
- **ครอบคลุม 26 หมวดหมู่วิชาชีพ :** ทั้งงานเทคนิค, UX Writing, กฎหมาย, การเงิน, การแพทย์, HR, การตลาด, ดีไซน์, บทสนทนา, ภาวะวิกฤต และสุขภาพจิต
- **โหลดเร็ว ไม่กิน token (Progressive Disclosure) :** แยกเนื้อหารายละเอียดไว้ในโฟลเดอร์ `references/` ทำให้ AI อ่านเฉพาะส่วนที่จำเป็นต้องใช้

---

## โครงสร้างไฟล์ (Universal Skill Structure)

```text
natural-thai/
├── SKILL.md                                 # ไฟล์คำสั่งหลักสำหรับ Agent (YAML Frontmatter + Core Directives)
├── references/                              # เอกสารคู่มืออ้างอิงเชิงลึก 26 หมวดหมู่
│   ├── thai-grammar-fundamentals.md         # หลักไวยากรณ์ไทยพื้นฐานและการเรียงรูปประโยค
│   ├── structure-and-meaning-preservation.md # กฎเหล็กการรักษาแก่นความหมาย 6 ประการ ป้องกัน Semantic Drift
│   ├── context-and-tone.md                  # การปรับระดับภาษา 5 ระดับตามบริบทและผู้รับสาร
│   ├── loanwords-and-spelling.md            # ตารางคำทับศัพท์ คำยืม และการเว้นวรรค
│   ├── word-blacklist.md                    # รายการคำต้องห้าม คำที่สะกดผิดบ่อย และคำทดแทน
│   ├── ux-writing-and-microcopy.md          # การเขียนข้อความในระบบ ปุ่ม CTA และ Error Message
│   ├── ux-ui-principles-and-heuristics.md   # กฎ 16 ข้อ (Laws of UX) และ Heuristics
│   ├── design-and-creative-guide.md         # คู่มือศัพท์และภาษาสำหรับสายงานออกแบบ
│   ├── industry-and-profession-guide.md     # คู่มือ 8 กลุ่มสาขาวิชาชีพเฉพาะทาง
│   ├── career-and-job-application-guide.md  # คู่มือการสื่อสารสมัครงาน อีเมล HR และเรซูเม่
│   ├── corporate-tact-and-managing-up.md    # การสื่อสารในองค์กรและการบริหารเจ้านาย
│   ├── sociolinguistics-and-generations.md  # ภาษาศาสตร์สังคมและการสื่อสาร 4 เจเนอเรชัน
│   ├── thai-humor-and-banter-guide.md       # คู่มืออารมณ์ขันไทยและการหยอกล้ออย่างสร้างสรรค์
│   ├── chat-and-messaging-cadence.md        # จังหวะการแชท (LINE, Slack, Discord)
│   ├── social-commerce-and-live-chat.md     # การตอบแชทขายของและการบริการลูกค้า
│   ├── screenplay-and-natural-dialogue.md   # บทสนทนาที่มีชีวิตและงานวรรณกรรม
│   ├── academic-and-scientific-prose.md     # ภาษาเชิงวิชาการและการเขียนบทคัดย่อ
│   ├── financial-and-data-standards.md      # มาตรฐานภาษาการเงินและข้อมูลตัวเลข
│   ├── crisis-communication.md              # การสื่อสารในภาวะวิกฤตและแถลงการณ์
│   ├── cross-cultural-communication.md      # การสื่อสารข้ามวัฒนธรรม
│   ├── accessibility-and-screen-reader.md   # ภาษาสำหรับการเข้าถึงและ Screen Reader
│   ├── mental-health-boundaries.md          # การให้กำลังใจและขอบเขตสุขภาพจิต
│   ├── multi-turn-continuity.md             # การรักษาความต่อเนื่องในบทสนทนายาว
│   ├── adversarial-benchmark-and-eval.md    # โจทย์ทดสอบความสมจริงของภาษา 10 หมวด
│   ├── linguistic-research.md               # เทคนิคการเขียนและ Checklist ความเป็นมนุษย์
│   └── examples.md                          # รวมตัวอย่าง Before / After ครบทุกสถานการณ์
├── README.md                                # เอกสารแนะนำโปรเจกต์และวิธีติดตั้ง
├── LICENSE                                  # สัญญาอนุญาต (MIT)
└── .gitignore                               # ละเว้นไฟล์ระบบและการทดสอบภายใน
```

---

## วิธีติดตั้งและใช้งาน (Universal Installation)

### 1. Claude Code

นำโฟลเดอร์ `natural-thai` ไปวางไว้ในโฟลเดอร์ `.claude/skills/` :

```bash
# ติดตั้งเฉพาะโปรเจกต์
mkdir -p .claude/skills
git clone https://github.com/vorrex-playground/natural-thai.git .claude/skills/natural-thai

# หรือติดตั้งใช้งานทุกโปรเจกต์ในเครื่อง
mkdir -p ~/.claude/skills
git clone https://github.com/vorrex-playground/natural-thai.git ~/.claude/skills/natural-thai
```

---

### 2. GitHub Copilot

นำโฟลเดอร์ `natural-thai` ไปวางไว้ในโฟลเดอร์ `.github/skills/` ของ repository :

```bash
mkdir -p .github/skills
git clone https://github.com/vorrex-playground/natural-thai.git .github/skills/natural-thai
```

---

### 3. Cursor / Windsurf / Cline / Roo Code

สามารถคัดลอกไฟล์ `SKILL.md` และโฟลเดอร์ `references/` ไปวางไว้ในโฟลเดอร์ Rules หรือ Skills ของโปรเจกต์ (เช่น `.cursor/rules/` หรือ `skills/natural-thai/`) หรือใส่ข้อความกำกับใน System Prompt ได้ทันที

```bash
mkdir -p skills
git clone https://github.com/vorrex-playground/natural-thai.git skills/natural-thai
```

---

### 4. Google Antigravity (AGY)

นำโฟลเดอร์ `natural-thai` ไปวางไว้ในโฟลเดอร์ `.agents/skills/` ของโปรเจกต์ หรือในโฟลเดอร์คอนฟิกหลักของเครื่อง :

```bash
# ติดตั้งเฉพาะโปรเจกต์
mkdir -p .agents/skills
git clone https://github.com/vorrex-playground/natural-thai.git .agents/skills/natural-thai

# ติดตั้งระดับเครื่อง (Global Level)
# Windows:
git clone https://github.com/vorrex-playground/natural-thai.git %USERPROFILE%\.gemini\config\skills\natural-thai
# macOS / Linux:
git clone https://github.com/vorrex-playground/natural-thai.git ~/.gemini/config/skills/natural-thai
```

---

### 5. ChatGPT / Claude.ai / Gemini (Web UI & LLMs ทั่วไป)

สามารถนำคำสั่งไปใช้งานกับ AI ทั่วไปได้ง่าย ๆ :
- **Custom Instructions / System Prompt :** คัดลอกข้อความในไฟล์ `SKILL.md` ไปใส่ในช่อง Custom Instructions ของบัญชี
- **Projects / Gems / Knowledge Base :** อัปโหลดไฟล์ `SKILL.md` และไฟล์ในโฟลเดอร์ `references/` เข้าไปเป็นความรู้ประจำโปรเจกต์

---

## ตัวอย่างการทำงาน

### การอธิบายเรื่องเทคนิค

**แบบเดิม (ภาษา AI) :**
> Docker เป็นแพลตฟอร์มโอเพนซอร์สที่ทำการจัดการ containerization ซึ่งมีบทบาทสำคัญอย่างยิ่งในภูมิทัศน์ของการพัฒนาซอฟต์แวร์สมัยใหม่ โดยทำให้นักพัฒนาสามารถดำเนินการแพ็กเกจแอปพลิเคชันพร้อมด้วย dependencies ทั้งหมดลงใน container ที่มีความเป็นเอกเทศ

**แบบที่ปรับแล้ว (natural-thai) :**
> Docker ช่วยให้เราห่อแอปทั้งหมด ทั้งโค้ด ทั้งของที่โค้ดต้องใช้ ไว้ในกล่องเดียว เรียกว่า container
>
> เหมือนกล่องข้าวที่ใส่ทุกอย่างครบ เปิดกินได้เลย ไม่ต้องไปหาข้าว หาแกง หากับข้าวแยก เครื่องไหนเปิดกล่องนี้ก็ใช้ได้เหมือนกันหมด

---

### ข้อความแจ้งเตือนในระบบ (UX Writing)

**แบบเดิม (ภาษา AI) :**
> เกิดข้อผิดพลาดในการตรวจสอบความถูกต้องของรหัสผ่านของท่าน กรุณาดำเนินการกรอกใหม่อีกครั้ง

**แบบที่ปรับแล้ว (natural-thai) :**
> รหัสผ่านไม่ถูกต้อง ตรวจสอบแล้วลองใหม่อีกครั้ง

---

## ผู้จัดทำและสัญญาอนุญาต

โปรเจกต์นี้จัดทำโดย **vorrex (Chatpisit Sukhom)** และเผยแพร่ภายใต้สัญญาอนุญาต [MIT License](./LICENSE) สามารถนำไปใช้งาน ปรับแต่ง และแชร์ต่อได้อย่างอิสระ
