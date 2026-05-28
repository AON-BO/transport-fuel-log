# ระบบบันทึกค่าน้ำมัน — รถขนส่ง
## Transport Fuel Log

> Web app บันทึกค่าน้ำมันจากบิลน้ำมันของรถขนส่งสินค้า  
> ทำงานได้โดยไม่ต้องติดตั้ง — เปิดในเบราว์เซอร์ได้เลย

🔗 **Live Demo:** https://aon-bo.github.io/transport-fuel-log/

---

## คุณสมบัติหลัก / Features

| ฟีเจอร์ | รายละเอียด |
|--------|-----------|
| 📝 บันทึกข้อมูล | กรอกข้อมูลบิลน้ำมัน พร้อมคำนวณอัตโนมัติ (กม./ลิตร, บาท/กม.) |
| 📋 รายการทั้งหมด | แสดง/แก้ไข/ลบทุก record พร้อม filter เดือนและทะเบียน |
| 📊 รายงานสรุป | KPI รายคัน, สรุป grouped by ประเภทรถ, แผนภูมิวงเงิน |
| ⚙️ ตั้งค่า | จัดการรายชื่อรถ/คนขับ และตั้งวงเงิน/เดือน |
| 📤 Export CSV | ดาวน์โหลด Excel-compatible พร้อม BOM ภาษาไทย |
| 📥 Import CSV | นำเข้าข้อมูลจาก CSV (รองรับคอลัมน์ไม่เรียงลำดับ) |
| 🖨️ พิมพ์รายงาน | Print-ready layout ซ่อน UI ที่ไม่จำเป็น |

---

## วิธีใช้งาน / How to Use

### แท็บ 1 — บันทึกข้อมูล

1. เลือก **ทะเบียนรถ** จาก dropdown (ชื่อคนขับจะกรอกให้อัตโนมัติ)
2. กรอก **เลขไมล์ก่อน / หลัง** เพื่อคำนวณระยะทาง
3. กรอก **ยอดรวม (บาท)** หรือ **ราคา/ลิตร + ลิตร** — ระบบจะคำนวณส่วนที่เหลือให้
4. กด **บันทึก** — แถบวงเงินประจำเดือนจะอัปเดตทันที

> **Tip:** กด `แก้ไข` ในแท็บรายการเพื่อโหลด record กลับมาแก้ไขในฟอร์ม

---

### แท็บ 2 — รายการทั้งหมด

- **กรอง** ตามเดือนหรือทะเบียนรถ
- **แก้ไข** หรือ **ลบ** ทีละ record
- ตารางเรียงตามวันที่ล่าสุดขึ้นก่อน

---

### แท็บ 3 — รายงานสรุป

| ส่วน | รายละเอียด |
|------|-----------|
| Filter บนสุด | กรองตาม **เดือน** และ **ทะเบียน** |
| KPI Cards | ยอดรวม, ลิตรรวม, กม./ลิตรเฉลี่ย, บาท/กม.เฉลี่ย |
| ตารางสรุปรายคัน | จัดกลุ่มตามประเภทรถ พร้อม subtotal และ grand total |
| แผนภาพวงเงิน | แสดง % การใช้วงเงินรายคัน (กรอง by ประเภทรถได้) |

> ใช้ **filter จาก–ถึง (ประเภทรถ)** เพื่อเลือกดูเฉพาะบางประเภทในตารางสรุปรายคัน

---

### แท็บ 4 — ตั้งค่า ⚙️

#### ตั้งค่าวงเงิน/เดือน
กรอกวงเงินสูงสุดต่อเดือนสำหรับแต่ละประเภทรถ แล้วกด **บันทึก**

| ประเภท | ค่าเริ่มต้น |
|--------|-----------|
| 6 ล้อ | 30,000 ฿ |
| 6 ล้อ HIAB | 30,000 ฿ |
| 10 ล้อ | 40,000 ฿ |
| 12 ล้อ | 40,000 ฿ |

#### จัดการรถและคนขับ
- **เพิ่มรถใหม่** — กรอกทะเบียน, ชื่อคนขับ, ประเภทรถ แล้วกด "เพิ่มรถ"
- **แก้ไข** — คลิก ✏️ แก้ไข ข้างรายการ แก้ข้อมูล แล้วกด "บันทึกการแก้ไข"
- **ลบ** — คลิก 🗑️ ลบ (ยืนยันก่อนลบ)
- **รีเซ็ต** — คืนกลับเป็นรายการรถเริ่มต้น

> การเปลี่ยนแปลงรายชื่อรถมีผลทันทีกับ dropdown ทุกที่ในโปรแกรม

---

### Import / Export CSV

#### Export
กด **📤 Export CSV** ในแท็บรายการ — ได้ไฟล์ `fuel_export.csv` เปิดด้วย Excel ได้โดยตรง (UTF-8 BOM)

#### Import
1. กด **📥 Import CSV** แล้วเลือกไฟล์
2. ระบบรองรับ header ไม่เรียงลำดับ และตัวเลขแบบ `4,000`
3. Row ที่มีทะเบียนขึ้นต้นด้วย `#` จะถูกข้ามโดยอัตโนมัติ

#### Template
กด **📄 Download Template** เพื่อดาวน์โหลด CSV ตัวอย่างพร้อม header ที่ถูกต้อง

**Columns ใน CSV:**
```
วันที่, เลขบิล, ทะเบียน, ชื่อคนขับ, ประเภท, เลขไมล์ก่อน, เลขไมล์หลัง,
ประเภทน้ำมัน, ราคาต่อลิตร, จำนวนลิตร, ยอดรวม, ระยะทาง, กม/ลิตร, บาท/กม
```

---

## Technical Reference

### Tech Stack
- **HTML5 + CSS3 + Vanilla JavaScript** — ไม่มี framework, ไม่มี build step
- **localStorage** — เก็บข้อมูลทั้งหมดในเครื่อง ไม่มี backend
- **GitHub Pages** — deploy โดยตรงจาก `main` branch

### localStorage Keys

| Key | Type | รายละเอียด |
|-----|------|-----------|
| `fuelRecords_v1` | `Record[]` | ข้อมูลบันทึกน้ำมันทั้งหมด |
| `budgetSettings` | `{[type]: number}` | วงเงิน/เดือน ที่ผู้ใช้แก้ไข |
| `vehicleSettings` | `Vehicle[]` | รายชื่อรถที่ผู้ใช้แก้ไข |

### Data Structures

```js
// Record
{
  id: number, no: number, date: 'YYYY-MM-DD', billNo: string,
  plate: string, name: string, type: string,
  odomBefore: number, odomAfter: number,
  fuelType: string, pricePerL: number, liters: number,
  totalPrice: number, distance: number, kmPerL: number, bahtPerKm: number
}

// Vehicle
{ plate: string, name: string, type: string }

// BudgetSettings
{ '6 ล้อ': number, '6 ล้อ HIAB': number, '10 ล้อ': number, '12 ล้อ': number }
```

### ประเภทรถที่รองรับ / Vehicle Types
```
TYPE_ORDER = ['6 ล้อ', '6 ล้อ HIAB', '10 ล้อ', '12 ล้อ']
```

### Key Functions

| Function | หน้าที่ |
|----------|--------|
| `submitForm()` | บันทึก / อัปเดต record |
| `renderList()` | render ตารางรายการทั้งหมด |
| `renderReport()` | render รายงานสรุปพร้อม filter |
| `renderVehicleSettings()` | render ตารางจัดการรถ |
| `populatePlateDropdown()` | rebuild dropdown ทะเบียนรถ |
| `populateFilters()` | rebuild filter dropdowns ทุกแท็บ |
| `exportCSV()` | สร้างและดาวน์โหลด CSV |
| `importCSV(input)` | อ่านและ merge ข้อมูลจาก CSV |
| `normHdr(h)` | normalize CSV header (lowercase + Thai chars only) |
| `saveVehicles()` | บันทึก VEHICLES ลง localStorage |
| `saveBudget()` | บันทึก BUDGET ลง localStorage |

### Date Formats
- เก็บใน storage: `YYYY-MM-DD`
- รับใน CSV: `D/M/YYYY` หรือ `YYYY-MM-DD`
- `normalizeDate()` แปลงทั้งสองรูปแบบให้เป็น `YYYY-MM-DD`

---

## การ Deploy / Deployment

Repository นี้ deploy บน GitHub Pages โดยอัตโนมัติจาก `main` branch

```
https://aon-bo.github.io/transport-fuel-log/
```

ไม่ต้องการ build step — แก้ไข `index.html` แล้ว push ได้เลย

---

## โครงสร้างไฟล์ / File Structure

```
transport-fuel-log/
├── index.html        # แอปทั้งหมดอยู่ในไฟล์เดียว (HTML + CSS + JS)
└── README.md         # เอกสารนี้
```

---

*ข้อมูลทั้งหมดเก็บในเบราว์เซอร์ของคุณ — ไม่มีการส่งข้อมูลออกไปที่ใด*
