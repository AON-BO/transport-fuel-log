---
name: fuel
description: โหลด context ของ project transport-fuel-log ให้ครบก่อนทำงาน ใช้ตอนเริ่ม session ใหม่ทุกครั้ง เพื่อไม่ต้องเสีย token อ่านไฟล์ซ้ำ
user-invocable: true
allowed-tools: Read Bash Grep
---

คุณกำลังทำงานกับ project **transport-fuel-log** — HTML app บันทึกค่าน้ำมันรถขนส่ง
ไฟล์หลักคือ `index.html` ไฟล์เดียว (vanilla HTML/CSS/JS, LocalStorage, GitHub Pages)

## Project Status
!`cat "C:/Users/chali/.claude/projects/c--Users-chali-OneDrive--------Projects-transport-fuel-log/memory/project_status.md"`

## Commits ล่าสุด
!`cd "c:/Users/chali/OneDrive/เอกสาร/Projects/transport-fuel-log" && git log --oneline -6`

## ฟังก์ชันหลักใน index.html (พร้อม line number)
!`cd "c:/Users/chali/OneDrive/เอกสาร/Projects/transport-fuel-log" && grep -n "^function " index.html`

## Storage Keys
- `fuelRecords_v1` — records ทั้งหมด
- `budgetSettings` — วงเงินที่ผู้ใช้แก้ไข (JSON)

## กฎการทำงาน
- แก้ไขเฉพาะจุดที่จำเป็น ไม่เพิ่ม feature ที่ไม่ได้ขอ
- Commit ทุกครั้งที่แก้เสร็จ แล้ว push ไป GitHub Pages
- ถามผู้ใช้ก่อนถ้าไม่แน่ใจว่าต้องการอะไร
