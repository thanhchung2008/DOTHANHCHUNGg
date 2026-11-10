# BÀI LÀM – HACKATHON 02

- **Mã đề:** 01
- **Họ tên:**Trần Đức Tài
- **Lớp:** HNKS26CNTT3
- **Link repository:**
- **Hệ điều hành (Windows/macOS):** Windows

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
pwd
ls -Recurse
mv .\ghi_chu_ban_giao.txt .\docs\
mkdir backup
cp .\data\dan_san_thang_10.xlsx .\backup\
cd logs
ls 
cd ..
Get-ChildItem -Recurse -Force

```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
Directory: C:\Users\hinat\Downloads\Luyen_Tap\starter-kit\starter-kit\san-bong-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-r---         11/3/2026   1:56 PM                backup
d-r---         11/3/2026   1:53 PM                data
d-r---         11/3/2026   1:55 PM                docs
d-r---         11/3/2026   1:53 PM                evidence
d-r---         11/3/2026   1:54 PM                logs
d-r---         11/3/2026   1:49 PM                web
-a----         11/3/2026   1:49 PM             76 .env
-a----         11/3/2026   1:49 PM           2409 bai_lam.md
-a----         11/3/2026   1:49 PM             22 temp_002.tmp


    Directory:
    C:\Users\hinat\Downloads\Luyen_Tap\starter-kit\starter-kit\san-bong-website\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   1:49 PM           6074 dan_san_thang_10.xlsx


    Directory:
    C:\Users\hinat\Downloads\Luyen_Tap\starter-kit\starter-kit\san-bong-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   1:49 PM           6074 dan_san_thang_10.xlsx


    Directory:
    C:\Users\hinat\Downloads\Luyen_Tap\starter-kit\starter-kit\san-bong-website\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   1:49 PM            154 ghi_chu_ban_giao.txt


    Directory:
    C:\Users\hinat\Downloads\Luyen_Tap\starter-kit\starter-kit\san-bong-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   1:49 PM            956 access.log


    Directory:
    C:\Users\hinat\Downloads\Luyen_Tap\starter-kit\starter-kit\san-bong-website\web


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-r---         11/3/2026   1:49 PM                images
-a----         11/3/2026   1:49 PM            590 app.js
-a----         11/3/2026   1:49 PM            529 index.html
-a----         11/3/2026   1:49 PM            460 style.css


    Directory:
    C:\Users\hinat\Downloads\Luyen_Tap\starter-kit\starter-kit\san-bong-website\web\images


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   1:49 PM           3101 logo-san-bong.png
```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell
Get-Content .\logs\access.log | Select-String "Status=500" > .\logs\loi_500.txt
Get-Content .\logs\loi_500.txt -Head 2

```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text
2026-10-28 08:24:34 POST /api/thanh-toan status=500
2026-10-28 08:28:45 POST /api/thanh-toan status=500

```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
(Get-Content .\logs\access.log | Select-String "Status=404").Count

```

```text
4

```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\tong_hop.ps1
```

### Nội dung file logs/tong_hop.txt

```text
=== BAO CAO SU CO WEBSITE ===

2026-10-28 08:07:39 GET /tin-tuc status=404
2026-10-28 08:13:01 GET /dat-san-cu status=404
2026-10-28 08:34:07 GET /images/san-7.jpg status=404
2026-10-28 08:57:24 GET /khuyen-mai status=404




Count    : 6
Average  : 
Sum      : 
Maximum  : 
Minimum  : 
Property : 

```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [x] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [x] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | --- | --- | --- |
| 1 | Network |logo không hiển thị | Mở vs code sửa lại cho đúng tên file logo |
| 2 | Console | Uncaught ReferenceError: hienThiBangGia is not defined | kiểm tra lại lỗi chính tả tên hàm trong `app.js` |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` 

![Lỗi Network](https://lens.usercontent.google.com/image?vsrid=CIyJjeiIpJ-XvgEQAhgBIiQzOTcwZjQ1NS1lNWY2LTRkYTMtYTg2YS0zZjY5NjgyNmU5NWYygQEiAnRhKCJCcwoubGZlLWR1bW15OjNlMWJmMDE2LWY4YTMtNDBjOC1iZmM3LWZkYTc1YjAzY2FkMBJBCj8vYm5zL3RhL2JvcmcvdGEvYm5zL2xlbnMtZnJvbnRlbmQtYXBpL3Byb2QubGVucy1mcm9udGVuZC1hcGkvNjFaBAoCdGE4xvGHrqzrlwM&gsessionid=Yb-6j66VyrNXf8tSlCObuu-h25dSXrlJmzqFt85SWOgoEFslrrUOrA)

![Lỗi Console](https://lens.usercontent.google.com/image?vsrid=COCAtb2x_d_voQEQAhgBIiQwMDdjYzA5Mi03OTc3LTRiNmQtOTQwNC01Yzg5NzVmYmUzZGIygwEiAnRhKIsBQnQKLmxmZS1kdW1teTo2ZjM1NmI5Yy0zNjAzLTRkMWQtYmI1Ny00ZmZhYWQ4OTdjYmYSQgpAL2Jucy90YS9ib3JnL3RhL2Jucy9sZW5zLWZyb250ZW5kLWFwaS9wcm9kLmxlbnMtZnJvbnRlbmQtYXBpLzE5MloECgJ0YTjr1_XRq-uXAw&gsessionid=rQuvBvomy8Kurg6p0z9eN7XH_DEEhTOTyVqdFVEUhM2TGOGQTP-BZQ)

### Báo cáo lỗi gửi trưởng nhóm

- **Context:** 
- **Expected:** 
- **Actual:** 
- **Log:** 

### Câu tìm kiếm Google

```text
(Ghi câu tìm kiếm vào đây – xoá dòng này)

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/dat_san_thang_10.xlsx`, không cần ghi vào đây.
