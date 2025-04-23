# BaiTapso5
Họ Tên SV: Chu Hoàng Huy

MSV: K215480106076

do kì này em học lại nên em lấy đề tài của kì trước em làm sql ạ

 # Yêu Cầu Bài Tập 
BÀI TẬP VỀ NHÀ 05, Môn Hệ quản trị csdl.
SUBJECT: Trigger on mssql
A.Trình bày lại đầu bài của đồ án PT&TKHT:
1. Mô tả bài toán của đồ án PT&TKHT, 
   đưa ra yêu cầu của bài toán đó
2. Cơ sở dữ liệu của Đồ án PT&TKHT :
   Có database với các bảng dữ liệu cần thiết (3nf),
   Các bảng này đã có PK, FK, CK cần thiết 
B. Nội dung Bài tập 05:
1. Dựa trên cơ sở là csdl của Đồ án
2. Tìm cách bổ xung thêm 1 (hoặc vài) trường phi chuẩn
   (là trường tính toán đc, nhưng thêm vào thì ok hơn,
    ok hơn theo 1 logic nào đó, vd ok hơn về speed)
   => Nêu rõ logic này!
3. Viết trigger cho 1 bảng nào đó, 
   mà có sử dụng trường phi chuẩn này,
   nhằm đạt được 1 vài mục tiêu nào đó.
   => Nêu rõ các mục tiêu 
4. Nhập dữ liệu có kiểm soát, 
   nhằm để test sự hiệu quả của việc trigger auto run.
5. Kết luận về Trigger đã giúp gì cho đồ án của em.

 
 # Bài Làm 
 Đề tài đồ án: Quản lý mượn trả sách thư viện
1. Mô tả bài toán
Xây dựng hệ thống quản lý mượn/trả sách tại thư viện, cho phép lưu thông tin sinh viên, sách, và các phiếu mượn trả. Hệ thống cần hỗ trợ theo dõi số ngày mượn và tình trạng sách đã trả hay chưa.
2. Thiết kế CSDL
Database: QLThuVien gồm 3 bảng chính:
SinhVien: MaSV (PK), HoTen, Lop

![image](https://github.com/user-attachments/assets/2aad26f1-982e-442e-8660-5f1f108019e0)

Sach: MaSach (PK), TenSach, TacGia

![image](https://github.com/user-attachments/assets/e28297fd-0753-476d-9291-4f80ea5185e2)

MuonTra MaPhieu (PK), MaSV (FK), MaSach (FK), NgayMuon, NgayTra, SoNgayMuon, TrangThai

![image](https://github.com/user-attachments/assets/dac41ca1-d2f3-4056-aaa6-4db984196a1b)

3. thêm trường phi chuẩn
  - Them truong phi chuan
Truong bo sung: SoNgayMuon va TrangThai trong bang MuonTra
Giai thich:
SoNgayMuon = DATEDIFF(NgayTra - NgayMuon): co the tinh toan duoc nhung duoc luu lai de tang toc cac truy van thong ke.
TrangThai: Xac dinh tinh trang muon-tra cua sach. (Da tra / Chua tra)

4. trigger sử dụng trường phi chuẩn

![image](https://github.com/user-attachments/assets/e03436e9-d11f-4ecf-800a-9794613dc80e)

nhập dữ liệu có kiểm soát để test 

![image](https://github.com/user-attachments/assets/206e11c2-6d2c-4cf9-b502-6a0d8f8d19b3)


#### 🔗 Link tải file SQL:
https://1drv.ms/u/c/d644b05ab59a11c4/EXxMV9VNHedIrbLFLAm4p6cBhUMvJapzxXjuMwJz67utjQ?e=BOV69f

# kết luận phn trigger giúp ích gì cho đồ án 
Việc sử dụng Trigger trong hệ thống quản lý mượn trả sách mang lại nhiều lợi ích thiết thực:

 Tự động hóa xử lý: Trigger giúp tự động cập nhật các trường như SoNgayMuon, TrangThai mà không cần thao tác thủ công hay viết thêm nhiều truy vấn mỗi lần dữ liệu thay đổi.

 Đảm bảo tính nhất quán dữ liệu: Trigger giúp kiểm soát logic nghiệp vụ chặt chẽ (ví dụ: không cho mượn nếu sách chưa được trả), tránh nhập sai dữ liệu.

 Tăng hiệu suất thống kê: Dữ liệu đã được chuẩn hóa và cập nhật sẵn, nên các truy vấn thống kê về thời gian mượn, tình trạng sách sẽ chạy nhanh và hiệu quả hơn.

 Giảm lỗi người dùng: Vì trigger xử lý tự động sau khi thao tác INSERT/UPDATE, nên người dùng không cần quan tâm tới việc điền chính xác các giá trị này.

Nhờ đó, Trigger góp phần nâng cao tính ổn định, an toàn và chuyên nghiệp cho hệ thống quản lý thư viện.




