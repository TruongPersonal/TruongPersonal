## Thuật ngữ cốt lõi
| Thuật ngữ      | Viết tắt | Ý nghĩa                                                       |
| :------------- | :------- | :------------------------------------------------------------ |
| **Clone**      |          | Hành động nhân bản toàn bộ kho chứa từ server về máy cá nhân  |
| **Repository** | **Rep ** | Kho lưu trữ chứa mã nguồn, lịch sử thay đổi và các nhánh      |
| **Commit**     |          | Ghi nhận một tập hợp các thay đổi vào lịch sử dự án (ủy thác) |
| **Version**    | **Ver**  | Một phiên bản cụ thể của mã nguồn tại một thời điểm           |
| **Timeline**   |          | Dòng thời gian hiển thị chuỗi các commit nối tiếp nhau        |
| **Revert**     | **Rev**  | Thao tác khôi phục mã nguồn về một phiên bản trước đó         |
## Khái niệm về VCS
> [!INFO] Định nghĩa
> **VCS (Version Control System)** là hệ thống kiểm soát các phiên bản phân tán mã nguồn mở. Nó hoạt động như một "cỗ máy thời gian" cho mã nguồn, lưu trữ mọi thay đổi và cho phép truy xuất bất cứ lúc nào

### Cơ chế hoạt động:
* **Lưu trữ toàn diện:** Lưu trữ tất cả các file và ghi lại chi tiết lịch sử thay đổi. Mỗi lần lưu lại thành công sẽ tạo ra một **Ver** mới
* **Luồng làm việc:** 
	1. Lập trình viên **Clone** mã nguồn từ **Repo** chính về máy local
    2. Thực hiện thay đổi và **Commit** để lưu trữ tạm thời hoặc đẩy lên server
    3. Đồng nghiệp có thể **Clone** hoặc cập nhật các thay đổi mới nhất này về máy của họ.

### Thông tin trong một Version:
Mỗi khi một **Ver** được lưu lại trên **Timeline**, hệ thống sẽ ghi nhận 4 thông tin quan trọng:
1. 📝 **Nội dung:** Chi tiết những dòng code bị thay đổi, thêm hoặc xóa
2. 🕒 **Thời gian:** Thời điểm chính xác thực hiện commit
3. 👤 **Tác giả:** Người thực hiện thay đổi đó
4. 💬 **Mô tả (Message):** Lý do tại sao thay đổi này được thực hiện

## Tác dụng của VCS

### Quản lý lịch sử & An toàn mã nguồn
- Lưu trữ không giới hạn các phiên bản của dự án
- Dễ dàng so sánh các thay đổi giữa các mốc thời gian
- Khả năng **Revert (Khôi phục)** cực nhanh khi mã nguồn gặp lỗi hoặc muốn hủy bỏ các thử nghiệm không thành công

### Tối ưu hóa cộng tác
- Việc chia sẻ code giữa các thành viên trở nên đơn giản và bảo mật (tùy chỉnh Public/Private)
- Nhiều người có thể cùng làm việc trên một file mà không sợ ghi đè mất công sức của nhau

## Mở rộng
> [!TIP] Mẹo hay
> Git hiện là hệ thống VCS phân tán phổ biến nhất thế giới nhờ tốc độ nhanh và khả năng quản lý nhánh (branching) cực kỳ linh hoạt