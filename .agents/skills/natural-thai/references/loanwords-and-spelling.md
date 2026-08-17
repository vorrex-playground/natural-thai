# คู่มือคำทับศัพท์ การสะกดคำ และการรักษา Syntax โค้ด (Loanwords & Technical Syntax)

> **เป้าหมายหลัก:** สะกดคำทับศัพท์ภาษาอังกฤษให้ถูกต้องตามมาตรฐาน และคงรูปศัพท์เฉพาะทางเทคนิคให้เป็นธรรมชาติสำหรับการทำงานจริงของมนุษย์สาย Tech, Design และ Business

---

## 1. รายการคำทับศัพท์มาตรฐาน (Standard Transliteration Whitelist)

| คำภาษาอังกฤษ | คำทับศัพท์ที่ถูกต้อง | หมายเหตุ |
|---|---|---|
| Check | **เช็ก** | ในบริบทโค้ดหรือชื่อตัวแปรให้คงรูปภาษาอังกฤษ |
| Update | **อัปเดต** | |
| Upload | **อัปโหลด** | |
| Version | **เวอร์ชัน** | |
| Project | **โปรเจกต์** | |
| Server | **เซิร์ฟเวอร์** | |
| Package | **แพ็กเกจ** | ในคำสั่ง npm/yarn ให้คงรูป `package.json` |
| Directory | **ไดเรกทอรี** | ในคำสั่ง CLI ให้คงรูป `dir`, `cd` |
| Application | **แอป / แอปพลิเคชัน** | |
| Email | **อีเมล** | |
| Link | **ลิงก์** | |
| Function | **ฟังก์ชัน** | ในโค้ดให้คงรูป `function` |
| Script | **สคริปต์** | |
| Login / Log in | **ล็อกอิน / เข้าสู่ระบบ** | |
| Post | **โพสต์** | |
| Comment | **คอมเมนต์** | |

---

## 2. กริยาภาษาพูดและคำทับศัพท์สายเทคนิค (Developer Tinglish Verbs)

| คำศัพท์ / สำนวน | ความหมายทางเทคนิค | ตัวอย่างการใช้งานจริงของมนุษย์ |
|---|---|---|
| **ยิง API** | Call / Send HTTP Request | *"ลองยิง endpoint นี้ดูยัง พ่น response กลับมาเป็นอะไร"* |
| **พ่น log / พ่น error** | Print / Output stack trace | *"service พ่น 500 ออกมารัว ๆ เลยพี่"* |
| **ยัด payload / mock** | Pass parameter / Mock data | *"ยัด mock data ก้อนนี้เข้าไปเทสก่อน"* |
| **ตบโค้ด / ตบ layout** | Adjust / Refactor slightly | *"ขอตบ format โค้ดให้ตรง lint แป๊บเดียว"* |
| **โค้ดชน / branch ชน** | Git merge conflict | *"branch ชนกับ main ตรง schema พอดี"* |
| **แตก / บึ้ม / ร่วง** | Service down / Build failed | *"CI แตกเพราะ test ไม่ผ่าน", "Prod ร่วงไป 2 นาที"* |
| **หลุด** | Memory leak / Uncaught edge case | *"เคสนี้หลุดไปถึง prod ได้ไงเนี่ย"* |
| **แกะบั๊ก / ไล่โค้ด** | Debug / Trace stack | *"เดี๋ยวช่วยแกะ log ย้อนหลังให้ครับ"* |
| **ดัน / ปล่อย** | Deploy / Push to environment | *"ดันขึ้น staging เรียบร้อยแล้วครับ"* |
| **ตัน / อืด** | Bottleneck / High latency | *"DB connection pool ตัน หน้าเว็บเลยอืด"* |

---

## 3. ข้อยกเว้นทางเทคนิคและการรักษาความปลอดภัยของ Syntax (Code Protection Guardrails)

กฎการเว้นวรรค 1 เคาะรอบภาษาอังกฤษและตัวเลข มีผลเฉพาะ **ข้อความบรรยายภาษาไทยทั่วไป** เท่านั้น:

### [ข้อควรระวัง] ข้อห้ามเด็ดขาด (Strict Exceptions):
ห้ามนำกฎการเว้นวรรคภาษาไทยไปใช้ภายในองค์ประกอบทางเทคนิคต่อไปนี้โดยเด็ดขาด:
1. **Code Blocks (```...```):** ห้ามแทรกช่องว่างในโค้ดทุกภาษา
2. **Inline Code (`...`):** ห้ามเว้นวรรค เช่น `get_user_id()` ห้ามแก้เป็น `get _ user _ id ()`
3. **Terminal Commands:** ห้ามเว้นวรรคในคำสั่ง เช่น `npm install --save-dev`
4. **File Paths & URLs:** เช่น `src/controllers/authController.ts`
5. **JSON Keys & Environment Variables:** เช่น `AUTH_SECRET_KEY`
6. **Regular Expressions (Regex):** ห้ามแทรกช่องว่างใน Pattern
