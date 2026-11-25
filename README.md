# HỆ THỐNG QUẢN LÝ QUÁN CAFE & TRÀ SỮA

Đồ án môn học xây dựng ứng dụng desktop quản lý vận hành quán Cafe – Trà sữa theo mô hình kiến trúc **3 lớp (3-Tier Architecture)** trên nền tảng **C# WinForms (.NET)** kết hợp **Microsoft SQL Server**.

---

## 1. Phân Công Thành Viên Nhóm

|  STT   | Họ và Tên                 | Phân Mảng Phụ Trách                    | Các Chức Năng Chính (03 Forms / Thành Viên)                                                                                                                                            |
| :----: | :------------------------ | :------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **01** | **Bùi Lên Hoàn**          | **Phần 1: Bán hàng & Khách hàng**      | • Lập hóa đơn & Order tại quầy (POS)<br>• Quản lý danh sách hóa đơn & Thanh toán<br>• Quản lý thông tin khách hàng & Tích điểm                                                         |
| **02** | **Nguyễn Tiến Nhật Minh** | **Phần 2: Thực đơn & Kho nguyên liệu** | • Quản lý danh mục đồ uống & bánh ngọt (`FrmDanhMucMon`)<br>• Quản lý thực đơn, giá bán & trạng thái (`FrmQuanLyMonAn`)<br>• Quản lý tồn kho & Lập phiếu nhập kho (`FrmKhoNguyenLieu`) |
| **03** | **Nguyễn Văn Lộc**        | **Phần 3: Bàn, Nhân sự & Thống kê**    | • Quản lý sơ đồ bàn & trạng thái phục vụ (`FrmQuanLyBan`) <br>• Quản lý hồ sơ nhân viên & phân quyền tài khoản (`FrmQuanLyNhanVien`) <br>• Báo cáo thống kê doanh thu & nguyên liệu   (`FrmThongKe`)                                            |

---

## 2. Công Nghệ & Kiến Trúc Hệ Thống

- **Ngôn ngữ & Giao diện:** C# (.NET WinForms)
- **Cơ sở dữ liệu:** Microsoft SQL Server (Tên CSDL: `QuanLyQuanAnDB`)
- **Thư viện kết nối:** `Microsoft.Data.SqlClient` (ADO.NET)
- **Kiến trúc 3 lớp (3-Tier):**
  - `DTO` (_Data Transfer Object_): Định nghĩa các đối tượng ánh xạ dữ liệu giữa các tầng.
  - `DAL` (_Data Access Layer_): Kết nối SQL Server qua `DatabaseHelper`, thực thi truy vấn tham số hóa (`SqlParameter`) chống SQL Injection và xử lý giao dịch (`SqlTransaction`).
  - `BUS` (_Business Logic Layer_): Kiểm tra tính hợp lệ dữ liệu và xử lý nghiệp vụ trước khi gọi xuống tầng `DAL`.
  - `Forms` (_Presentation Layer_): Giao diện tương tác người dùng WinForms.

---

## 3. Cấu Trúc Thư Mục Dự Án

```text
XayDungQuanLiCafe/
├── Database/
│   └── ScriptDB.sql              # Script khởi tạo CSDL QuanLyQuanAnDB & dữ liệu mẫu quán Cafe
├── src/
│   ├── DTO/                      # Các lớp đối tượng dữ liệu (MenuInventoryDTO, ...)
│   ├── DAL/                      # Kết nối DB (DatabaseHelper.cs) & truy vấn SQL
│   ├── BUS/                      # Xử lý nghiệp vụ
│   ├── Forms/                    # Giao diện WinForms (FrmDangNhap, FrmMain và 9 Form chức năng)
│   ├── Program.cs                # Điểm khởi chạy ứng dụng
│   └── hoccsharp.csproj          # File cấu hình dự án .NET
└── README.md                     # Tài liệu hướng dẫn dự án
```
