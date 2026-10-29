Bài 8 : Phân tích lỗ hổng cấu hình quyền chia sẻ và rò rỉ dữ liệu

Phần 1: Phân tích lỗ hổng

1. Nguồn gốc gây rò rỉ dữ liệu:

* Dòng log gây rò rỉ: Dòng 1 (08:15 T2 - file campuspay_beta_users.xlsx).
* Nguyên nhân & Cơ chế: Vi phạm Quy tắc Cờ Đỏ do dùng quyền Editor kết hợp với Anyone with the link trên file chứa SĐT và số dư. Link trở thành công khai, cho phép bất kỳ ai nhấp vào trên Facebook đều có thể xem, tải và sao chép dữ liệu ẩn danh.

2. 3 giả thuyết về Email người lạ truy cập file campuspay_api_keys.txt (10:00 T3):

* Giả thuyết 1: Tài khoản Email B bị chiếm đoạt hoặc quên đăng xuất trên thiết bị công cộng.
* Giả thuyết 2: Chủ tài khoản Email B tự tải file hoặc copy API key rồi gửi cho người lạ.
* Giả thuyết 3: Trưởng nhóm chưa tắt tùy chọn cho phép Editor tự ý phân quyền và thêm người mới.

Phần 2: Sửa lỗi & Nghiệm thu

3. Bảng cấu hình quyền chia sẻ đúng chuẩn:

| Tên file | Phạm vi đúng | Quyền đúng |
| --- | --- | --- |
| campuspay_beta_users.xlsx | Restricted | Editor (người nhập liệu) / Viewer (người chỉ xem) |
| campuspay_api_keys.txt | Restricted | Viewer (chỉ nhân sự kỹ thuật cần dùng key) |
| slide_pitch_v8.pptx | Restricted | Commenter (để nhận góp ý) / Viewer (khi trình chiếu) |

Giải thích: File chứa dữ liệu cá nhân và API key phải chọn Restricted để bắt buộc xác thực danh tính. Slide chỉ cần quyền Commenter để tránh bị sửa hỏng định dạng.

4. Bẫy dữ liệu và quản lý quyền:

* Vô hiệu hóa link cũ nhanh nhất: Đổi phạm vi chia sẻ từ Anyone with the link về Restricted.
* Dùng Set Expiration Date khi: Chia sẻ tài liệu cho cộng tác viên hoặc đối tác trong thời hạn cố định (như 7 ngày), hệ thống sẽ tự động thu hồi quyền khi hết giờ.
