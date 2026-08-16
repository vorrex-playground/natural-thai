# natural-thai

Skill สำหรับ AI Coding Assistant และ Agent เพื่อให้เขียนและตอบเป็นภาษาไทยที่เป็นธรรมชาติ อ่านเข้าใจง่าย สื่อสารเหมือนคนทำงานจริง ๆ คุยกัน โดยไม่ใช้สำนวนแข็งทื่อหรือโครงสร้างประโยคแปลตรงตัวแบบ AI

โปรเจกต์นี้สร้างขึ้นตามมาตรฐาน **Agent Skills Open Standard** (agentskills.io) ใช้งานได้กับ Google Antigravity, Claude Code, GitHub Copilot, Cursor, Cline รวมถึง LLMs ทั่วไปอย่าง ChatGPT, Claude.ai และ Gemini *(อยู่ระหว่างการพัฒนา)*

---

## จุดเด่น

- **ภาษาเป็นธรรมชาติ :** ตัดโครงสร้างประโยคแปลอังกฤษตรงตัว ประโยคกรรมที่ฝืนธรรมชาติ ("ถูก...") และคำเชื่อมทางการซ้ำซาก
- **ปรับระดับภาษาตามบริบท (Adaptive Tone) :** ปรับระดับภาษาให้เข้ากับผู้รับสาร ทั้งการคุยกับหัวหน้า ลูกค้า เพื่อนร่วมงาน หรือคนทั่วไป
- **คำทับศัพท์และการเว้นวรรคที่ถูกต้อง :** ยึดตามหลักเกณฑ์ราชบัณฑิตยสภา (เช่น เช็ก, อัปเดต, โปรเจกต์, เซิร์ฟเวอร์, ลิงก์) พร้อมเว้นวรรคระหว่างภาษาไทย ภาษาอังกฤษ ตัวเลข และไม้ยมก (ๆ) ให้อ่านสบายตา
- **ครอบคลุมงานเทคนิคและ UX Writing :** มีแนวทางการอธิบายเรื่องเทคนิค การแจ้งเตือนข้อผิดพลาด (Error Message) และข้อความบนหน้าจอระบบ (Microcopy)
- **โหลดเร็ว ไม่กิน token (Progressive Disclosure) :** แยกเนื้อหารายละเอียดไว้ในโฟลเดอร์ `references/` ทำให้ AI อ่านเฉพาะส่วนที่จำเป็นต้องใช้

---

## โครงสร้างไฟล์

```text
natural-thai/
├── SKILL.md                          # ไฟล์คำสั่งหลักสำหรับ Agent
├── references/                       # เอกสารอ้างอิงและคู่มือแบบละเอียด
│   ├── context-and-tone.md          # การปรับภาษาและระดับความเป็นทางการตามบริบท
│   ├── examples.md                  # ตัวอย่างคู่เทียบ ก่อน / หลัง แบบ AI vs แบบคนเขียน
│   ├── loanwords-and-spelling.md    # ตารางคำทับศัพท์และหลักการเว้นวรรค
│   ├── ux-writing-and-microcopy.md  # การเขียนข้อความในระบบและปุ่มสั่งการ
│   └── word-blacklist.md            # รายการคำและวลีที่ควรเลี่ยง
├── .agents/skills/natural-thai/      # โฟลเดอร์สำหรับ Google Antigravity
├── README.md                         # เอกสารแนะนำโปรเจกต์
├── LICENSE                           # สัญญาอนุญาต (MIT)
└── .gitignore
```

---

## วิธีติดตั้งและใช้งาน

### 1. Google Antigravity (AGY)

#### ติดตั้งเฉพาะโปรเจกต์ (Workspace Level)
นำโฟลเดอร์ `natural-thai` ไปวางไว้ในโฟลเดอร์ `.agents/skills/` ที่ root ของโปรเจกต์ :

```bash
# อยู่ที่ root ของโปรเจกต์คุณ
mkdir -p .agents/skills
git clone https://github.com/vorrex-playground/natural-thai.git .agents/skills/natural-thai
```

#### ติดตั้งแบบใช้งานได้ทุกโปรเจกต์ (Global Level)
นำไปวางไว้ที่โฟลเดอร์การตั้งค่าหลักของเครื่อง :

- **Windows :** `%USERPROFILE%\.gemini\config\skills\natural-thai\`
- **macOS / Linux :** `~/.gemini/config/skills/natural-thai/`

```bash
git clone https://github.com/vorrex-playground/natural-thai.git ~/.gemini/config/skills/natural-thai
```

---

### 2. Claude Code

นำโฟลเดอร์ `natural-thai` ไปวางไว้ในโฟลเดอร์ `.claude/skills/` :

```bash
# ใช้งานเฉพาะโปรเจกต์
mkdir -p .claude/skills
git clone https://github.com/vorrex-playground/natural-thai.git .claude/skills/natural-thai

# หรือใช้งานทุกโปรเจกต์
mkdir -p ~/.claude/skills
git clone https://github.com/vorrex-playground/natural-thai.git ~/.claude/skills/natural-thai
```

---

### 3. GitHub Copilot

นำโฟลเดอร์ `natural-thai` ไปวางไว้ในโฟลเดอร์ `.github/skills/` ของ repository :

```bash
mkdir -p .github/skills
git clone https://github.com/vorrex-playground/natural-thai.git .github/skills/natural-thai
```

---

### 4. Cursor / Windsurf / Cline / Roo Code

สามารถคัดลอกไฟล์ `SKILL.md` และโฟลเดอร์ `references/` ไปวางไว้ในโฟลเดอร์ Rules หรือ Skills ของโปรเจกต์ (เช่น `.cursor/rules/` หรือ `skills/natural-thai/`) หรือใส่ข้อความกำกับใน System Prompt ได้ทันที

---

### 5. ChatGPT / Claude.ai / Gemini (Web UI & LLMs ทั่วไป)

สามารถนำคำสั่งไปใช้งานกับ AI ทั่วไปได้ง่าย ๆ 2 วิธี :
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
