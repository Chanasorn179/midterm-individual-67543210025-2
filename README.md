# 📚 Library Management System – Monolithic and Layered Architecture

## 📋 Project Information

* **Student Name:** นาย ชนสรณ์ บุตรถา
* **Student ID:** 67543210025-2
* **Course:** ENGSE207 Software Architecture

---

## 🏗️ Architecture Style

**Layered Architecture (3-tier)**

ระบบถูกออกแบบโดยแยกความรับผิดชอบออกเป็น 3 ชั้นหลัก ได้แก่

1. **Presentation Layer** – จัดการ HTTP Request/Response และ Routing
2. **Business Logic Layer** – จัดการ Business Rules และ Validation
3. **Data Access Layer** – จัดการการเข้าถึงฐานข้อมูล (SQLite)

---

## 📂 Project Structure

```
midterm-individual-67543210025-2/
├── src/
│   ├── presentation/              # Presentation Layer
│   │   ├── routes/                # กำหนด API routes
│   │   ├── controllers/           # จัดการ HTTP request/response
│   │   └── middlewares/           # Error handling
│   │
│   ├── business/                  # Business Logic Layer
│   │   ├── services/              # Business logic
│   │   └── validators/            # Validation rules
│   │
│   └── data/                      # Data Access Layer
│       ├── repositories/          # Database operations (CRUD)
│       └── database/              # SQLite connection
│
├── server.js                      # Application entry point
├── package.json
├── README.md
└── ARCHITECTURE.md
```

---

## 🎯 Refactoring Summary

### 🔴 ปัญหาของ Monolithic (เดิม)

* โค้ดทั้งหมดอยู่ในไฟล์เดียว ทำให้ไฟล์มีขนาดใหญ่และอ่านยาก
* Business Logic ปะปนกับ HTTP handling และ SQL queries
* แก้ไขโค้ดส่วนหนึ่งอาจกระทบส่วนอื่นโดยไม่ตั้งใจ
* ยากต่อการทดสอบแยกส่วน (Unit Test)

---

### 🛠️ วิธีแก้ไขด้วย Layered Architecture

* แยก **Presentation Layer** เพื่อดูแลเฉพาะการรับ–ส่ง HTTP
* ย้าย Business Rules และ Validation ไปไว้ที่ **Business Logic Layer**
* แยก SQL และการเข้าถึงฐานข้อมูลไปไว้ที่ **Data Access Layer**
* กำหนดทิศทางการเรียกใช้งานให้เป็นลำดับชั้น (Controller → Service → Repository)

---

### ✅ ประโยชน์ที่ได้รับ

* โค้ดอ่านง่ายและเป็นระบบมากขึ้น
* แก้ไขหรือขยายระบบได้ง่าย
* สามารถทดสอบแต่ละ Layer แยกจากกันได้
* รองรับการทำงานร่วมกันเป็นทีม
* สอดคล้องกับหลักการ Separation of Concerns

---

## 🚀 How to Run

```bash
# 1. Clone repository
git clone <your-repo-url>

# 2. Install dependencies
npm install

# 3. Run server
npm start

# 4. Open browser
http://localhost:3000
```

---

## 📝 API Endpoints

| Method | Endpoint                | Description             |
| ------ | ----------------------- | ----------------------- |
| GET    | `/api/books`            | ดึงข้อมูลหนังสือทั้งหมด |
| GET    | `/api/books/:id`        | ดึงข้อมูลหนังสือตาม ID  |
| POST   | `/api/books`            | เพิ่มหนังสือใหม่        |
| PUT    | `/api/books/:id`        | แก้ไขข้อมูลหนังสือ      |
| PATCH  | `/api/books/:id/borrow` | ยืมหนังสือ              |
| PATCH  | `/api/books/:id/return` | คืนหนังสือ              |
| DELETE | `/api/books/:id`        | ลบหนังสือ               |

---

## 📌 หมายเหตุ

* ไฟล์ฐานข้อมูล `library.db` เป็น runtime data ไม่ควร commit ลง GitHub
* รายละเอียดเชิงลึกของสถาปัตยกรรมดูได้ที่ไฟล์ `ARCHITECTURE.md`

---

**รายวิชา:** ENGSE207 Software Architecture<br>
**รูปแบบงาน:** Midterm Practical Exam (Individual)
