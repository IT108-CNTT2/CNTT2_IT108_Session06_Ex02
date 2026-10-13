## **Phần 1: Phân tích sự cố**

* **Sai lầm của An:** An đã sử dụng nhầm lệnh tìm kiếm **cấu trúc file** thay vì **nội dung bên trong file**.  
* **Phân biệt bản chất câu lệnh:**  
  * **`Get-ChildItem`** (alias: `ls`, `dir`): Dùng để tìm kiếm **tên file hoặc thư mục** dựa trên đường dẫn hoặc phần lọc (ví dụ tìm file tên `*404*`). Vì file log có tên là `access.log` chứ không chứa chữ "404" trong tên, lệnh này trả về kết quả trống.  
  * **`Select-String`**: Dùng để tìm kiếm **chuỗi văn bản/nội dung** bên trong các file (tương đương với lệnh `grep` trên Linux/Git Bash). Đây mới là công cụ đúng để quét các dòng log lỗi.

## **Phần 2: Sửa lỗi & Hoàn thiện lệnh**

Để lọc các dòng chứa chữ **"ERROR"** từ file `access.log` và hiển thị kèm số dòng, sử dụng lệnh `Select-String`:

Select-String \-Path access.log \-Pattern "ERROR"  
"# CNTT2_IT108_Session06_Ex02" 
