# Mini-Project-group-1-sec-1

---

#  AUTOMATED FILE RENAME FOR GOOGLE DRIVE

> **โปรแกรมเปลี่ยนชื่อไฟล์ภาพถ่ายทางวิทยาศาสตร์ (SEM) อัตโนมัติบน Google Drive**
> 
> รายงานและซอร์สโค้ดนี้เป็นส่วนหนึ่งของวิชา **CP352301 การเขียนโปรแกรมสคริปต์ (Script Programming)**
> 
> สาขาวิชาวิทยาการคอมพิวเตอร์ วิทยาลัยการคอมพิวเตอร์ มหาวิทยาลัยขอนแก่น
> 
> 

---

##  สมาชิกกลุ่ม (Group Members)

| รหัสนักศึกษา | ชื่อ - นามสกุล | กลุ่มเรียน (Section) | บทบาทหน้าที่ |
| :---: | :--- | :---: | :--- |
| 683380576-2 | นายธนธรณ์ ผาลัง | Sec 1 | Planner (วางแผน) / Debugger (แก้บั๊ก) |
| 683380584-3 | นายพีรพล พรหมมิ | Sec 1 | Coder (โค้ด) |

* **อาจารย์ประจำวิชา:** ผศ.ดร. บุญทรัพย์ ไวคำ



---

##  ที่มาและวัตถุประสงค์ของโครงงาน (Project Overview)

การจัดการภาพถ่ายจากกล้องจุลทรรศน์อิเล็กตรอน (Scanning Electron Microscope: SEM) ในงานวิจัยด้านธรณีวิทยา มักพบปัญหาชื่อไฟล์ดั้งเดิมที่เป็นรหัสตัวเลขเรียงลำดับ เช่น `1.tif`, `1_001.tif` ซึ่งไม่ระบุชื่อตัวอย่างหิน และตำแหน่งจุดถ่าย

โครงงานนี้จึงพัฒนาสคริปต์ Python สำหรับรันบน Google Colab เพื่อ:

1. สกัดค่ากำลังขยายจากบริเวณส่วนล่างของภาพ SEM ด้วยเทคโนโลยี **EasyOCR**

2. ดึงข้อมูลชื่อตัวอย่างหินจาก **Google Sheet** โดยจับคู่กับ `Date` และ `File ID`

3. คำนวณลำดับจุดถ่าย (Spot) และลำดับกำลังขยาย (Sequence) ตาม Logic การลด/เพิ่มของกำลังขยาย


4. ดำเนินการเปลี่ยนชื่อไฟล์บน **Google Drive** ให้อยู่ในรูปแบบมาตรฐานอัตโนมัติ: `[ชื่อตัวอย่าง]-[ลำดับจุด].[ลำดับซูม]_X[กำลังขยาย].[นามสกุลไฟล์]` (เช่น `PK1-1.2_X250.tif`)



---

##  Group Learning Outcomes (LO Alignment)

โครงงานนี้ออกแบบซอร์สโค้ดให้ครอบคลุมผลการเรียนรู้ (Learning Outcomes) หลักดังนี้:

* **LO1: Immutable Data Types & Data Structures**
* การใช้ `Tuple` สำหรับกำหนดพิกัดคงที่ (`CROP_BOUNDS`) เพื่อป้องกันการแก้ไขค่าโดยไม่ตั้งใจ
* การใช้ `Tuple (date_key, file_id)` เป็น Immutable Key ใน Dictionary




* **LO2: List Manipulations & Sequence Operations**
* การใช้ List สำหรับเรียงลำดับโฟลเดอร์/ไฟล์ภาพด้วย `.sort()`
* การจัดการคิวเปลี่ยนชื่อไฟล์ด้วย `.append()`, `.remove()`, `.clear()` และการนับปริมาณข้อมูลด้วย `len()`


* **LO3: Interactive Control Flow**
* การสร้างเมนูควบคุม CLI ผ่าน `while True` loop ร่วมกับ Multi-way Conditionals (`if / elif / else`)


* **LO4: Defensive Programming & Error Handling**
* การใช้ Guard Clauses และ Membership Check (`in` / `not in`) เพื่อตรวจสอบ Input, ป้องกัน `IndexError`, `KeyError`, และจัดการไฟล์ภาพชำรุด




* **LO5: AI Ethics & Explainable AI (XAI)**
* ระบบแสดงตัวอย่างแผนการเปลี่ยนชื่อไฟล์ (Dry Run / Preview) และคืนค่าสตริง OCR ต้นฉบับร่วมกับตัวเลข เพื่อสร้างความโปร่งใสก่อนเปลี่ยนชื่อจริง





---

##  Kanban Backlog Run (Development Cycles)

| Task Card | รายละเอียด Task | สถานะ (Status) | LO Alignment |
| --- | --- | --- | --- |
| **Task 1** | Setup Environment & Google Sheet Connection | **[ DONE ]** | **LO1, LO4** |
| **Task 2** | EasyOCR Integration & Magnification Parser | **[ DONE ]** | **LO1, LO4** |
| **Task 3** | File Scanning & ID Grouping Engine | **[ DONE ]** | **LO2** |
| **Task 4** | Spot & Sequence Tracking Logic Engine | **[ DONE ]** | **LO1, LO2** |
| **Task 5** | Interactive Menu & Defensive Removal | **[ DONE ]** | **LO2, LO3, LO4** |
| **Task 6** | Safe Execution & File Rename Action | **[ DONE ]** | **LO4** |
| **Task 7** | AI Ethics & Responsible AI Audit | **[ DONE ]** | **LO5** |

---

##  Group Assessments & Peer Evaluation

บันทึกผลการประเมินตนเองและเพื่อนร่วมกลุ่ม (คะแนนเต็ม 10)

### 1. การประเมินตนเอง (Self-Assessment)

| รหัสนักศึกษา | ชื่อ - นามสกุล | ความตรงต่อเวลา | คุณภาพงาน | การสื่อสาร | การมีส่วนร่วม |
| --- | --- | --- | --- | --- | --- |
| `683380584-3` | นายพีรพล พรหมมิ | 10 | 8 | 10 | 8 |
| `683380576-2` | นายธนธรณ์ ผาลัง | 7 | 7 | 6 | 8 |

### 2. การประเมินเพื่อนร่วมกลุ่ม (Peer-Assessment)

| ผู้ประเมิน | ผู้ถูกประเมิน | ความตรงต่อเวลา | คุณภาพงาน | การสื่อสาร | การมีส่วนร่วม |
| --- | --- | --- | --- | --- | --- |
| นายพีรพล พรหมมิ | นายธนธรณ์ ผาลัง | 9 | 10 | 8 | 10 |
| นายธนธรณ์ ผาลัง | นายพีรพล พรหมมิ | 9 | 10 | 8 | 10 |

---

##  Group Grading Rubric (เกณฑ์การวัดผลโครงงาน)

| หมวดหมู่การประเมิน | รายละเอียดเกณฑ์ (Criteria) | น้ำหนัก |
| :--- | :--- | :---: |
| **1. Technical Implementation** | มีการประยุกต์ใช้ Data Structure (Tuple, List, Dict) และ Control Flow ตามเกณฑ์ LO1-LO3 อย่างถูกต้อง | 30% |
| **2. Defensive Programming** | มีระบบ Guard Clauses, Exception Handling และการตรวจสอบภาพ/ข้อมูลชำรุด (LO4) | 25% |
| **3. AI & OCR Integration** | การใช้ EasyOCR สกัดข้อมูลข้อความ ร่วมกับ XAI Verification (LO5) | 20% |
| **4. Code Quality & Clean Code** | การแยก Modular Function, Single Responsibility Principle และการใส่ Type Hints | 15% |
| **5. Collaboration & Documentation** | เอกสารโครงงาน (PDF/README), Kanban Tracking และผลการประเมินกลุ่ม | 10% |
---


ลิงก์เอกสารที่เกี่ยวข้อง : <br>
* [Canva Presentation](https://canva.link/14gmfiboqb8s86u)
* [Project Document](https://drive.google.com/drive/folders/1EaSwRU2gAQIWgEvYskcnzQaVyWkXQnMT)
* [โฟลเดอร์ตัวอย่าง](https://drive.google.com/drive/folders/1EaSwRU2gAQIWgEvYskcnzQaVyWkXQnMT)
* [Self-Assessment](https://docs.google.com/spreadsheets/d/1jX7Q0Kz7-gCyZgpaXxYjq70AVYcW8kfg/edit?usp=sharing&ouid=111380127827180933816&rtpof=true&sd=true)
* [Kanban](https://colab.research.google.com/drive/10l1ZIAGxo2SMxSOKydHvYfSMhkC7wPjJ?usp=sharing)
