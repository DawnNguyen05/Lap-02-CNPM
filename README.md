
# 🏨 Hotel Reservation System

Hệ thống **Quản lý Đặt phòng Khách sạn (Hotel Reservation System)** giúp khách hàng đặt phòng trực tuyến, quản lý đặt phòng, thanh toán, và hỗ trợ nghiệp vụ cho nhân viên khách sạn (lễ tân, quản lý, buồng phòng).  
Dự án được phát triển theo **mô hình Agile – Scrum**, triển khai và theo dõi tiến độ bằng **Jira Software**.

---

## 📘 Mục tiêu dự án
- Xây dựng hệ thống đặt phòng khách sạn hiện đại, có khả năng mở rộng và dễ bảo trì.  
- Cung cấp trải nghiệm người dùng tốt cho khách hàng (Guest).  
- Hỗ trợ nhân viên khách sạn (Receptionist, Manager, Housekeeping) trong quy trình quản lý vận hành.  
- Tích hợp thanh toán trực tuyến và báo cáo doanh thu.

---

## 👥 Đối tượng & Vai trò
| Vai trò | Chức năng chính |
|----------|------------------|
| **Guest (Khách hàng)** | Tìm phòng, đặt phòng, thanh toán online, xem lịch sử đặt phòng |
| **Receptionist (Lễ tân)** | Check-in / Check-out, quản lý đặt phòng |
| **Manager (Quản lý)** | Quản lý phòng & giá, xem báo cáo doanh thu |
| **Housekeeping (Buồng phòng)** | Cập nhật trạng thái phòng, quản lý danh sách phòng cần dọn |
| **Payment Gateway** | Xử lý giao dịch thanh toán online |

---

## 🧩 Chức năng chính (Use Cases)

### 👤 Guest
- Đăng ký / Đăng nhập tài khoản  
- Tìm phòng trống, xem chi tiết phòng  
- Đặt phòng trực tuyến  
- Thanh toán online (qua cổng thanh toán)

### 🛎️ Receptionist
- Check-in / Check-out khách hàng  
- Tra cứu và xác nhận đặt phòng  

### 🧹 Housekeeping
- Quản lý danh sách phòng cần dọn  
- Cập nhật trạng thái phòng

### 📊 Manager
- Quản lý loại phòng, giá phòng  
- Xem báo cáo doanh thu theo tháng  

---

## 🧠 UML Design

### 1️⃣ Use Case Diagram
Các tác nhân chính: Guest, Receptionist, Manager, Payment Gateway, Housekeeping.  
Các use case tiêu biểu:
- Tìm phòng, Xem chi tiết phòng  
- Đặt phòng online  
- Thanh toán online  
- Check-in / Check-out  
- Quản lý phòng & giá  
- Báo cáo doanh thu  
- Quản lý buồng phòng  

### 2️⃣ Sequence Diagrams
- **Đặt phòng online**  
  1. Guest chọn phòng → Hệ thống giữ phòng (hold)  
  2. Guest nhập thông tin & thanh toán  
  3. Payment Gateway xác nhận → Gửi email xác nhận  

- **Check-in / Check-out (Lễ tân)**  
  1. Receptionist tra cứu mã đặt phòng  
  2. Check-in: gán phòng thực tế, cập nhật trạng thái  
  3. Check-out: tổng hợp chi phí, thu tiền, cập nhật buồng phòng  

---

## 🧮 Cấu trúc Cơ sở dữ liệu (ERD)

**Các bảng chính:**

| Bảng | Mô tả |
|------|-------|
| `Guest` | Thông tin khách hàng |
| `RoomType` | Loại phòng (tên, giá, sức chứa, mô tả) |
| `Room` | Thông tin phòng cụ thể |
| `Reservation` | Đặt phòng (guest, room, staff, ngày, trạng thái) |
| `Payment` | Thanh toán (số tiền, phương thức, trạng thái) |
| `Staff` | Nhân viên (tên, vai trò, tài khoản) |

**Quan hệ:**
- Guest 1–N Reservation  
- RoomType 1–N Room  
- Room 1–N Reservation  
- Reservation 1–N Payment  
- Staff 1–N Reservation  

---

## ⚙️ Công nghệ sử dụng
| Thành phần | Công nghệ / Công cụ |
|-------------|--------------------|
| **Frontend** | React / Next.js, TailwindCSS |
| **Backend** | Node.js (Express) hoặc Spring Boot |
| **Database** | MySQL / PostgreSQL |
| **Authentication** | JWT (JSON Web Token) |
| **Payment** | Cổng thanh toán tích hợp (VD: Stripe, VNPay sandbox) |
| **CI/CD** | GitHub Actions |
| **Project Management** | Jira Software (Agile Scrum) |
| **Design & UML** | PlantUML |

---

## 🚀 Quy trình phát triển (Agile – Scrum)

### 🗓️ Product Backlog
- Auth – Đăng ký/Đăng nhập khách hàng  
- Search – Tìm phòng & xem chi tiết phòng  
- Booking & Payment – Đặt phòng & thanh toán online  
- Check-in / Check-out – Quản lý bởi lễ tân  
- Room & Price Management – Quản lý phòng & giá  
- Reporting – Báo cáo doanh thu  
- Housekeeping – Quản lý buồng phòng

### 🧭 Sprint Plan
| Sprint | Nội dung chính |
|---------|----------------|
| **Sprint 1** | Auth, Tìm phòng, Xem chi tiết phòng |
| **Sprint 2** | Đặt phòng & Giữ chỗ |
| **Sprint 3** | Thanh toán, Check-in / Check-out |
| **Sprint 4** | Báo cáo, Housekeeping, Tối ưu & Release |

### 🪄 Jira Workflow
**Board Columns:**  
`To Do → In Progress → Code Review → Testing → Done`

Mỗi User Story mô tả theo format:  
`As a [role], I want [function], so that [benefit].`

---

## 🔄 Tích hợp GitHub ↔ Jira
- Mỗi issue trong Jira có **issue key** (ví dụ: `HRS-123`).  
- Mỗi commit trên GitHub được gắn issue key để tự động liên kết.

### Cấu trúc commit message:
```bash
HRS-123 Add: Booking use case diagram
# hoặc dùng Smart Commit:
HRS-123 #comment Added booking diagram #time 30m #transition "In Review"
