## 0. Thuật ngữ
1. **Clone:** Nhân bản
2. **Repository - _Repo_:** Kho chứa mã nguồn
3. **Commit:** Ủy thác
4. **Version - _Ver_:** Phiên bản
5. **Timeline:** Dòng thời gian
6. **Revert - _Rev_:** Khôi phục

---
## 1. Khái niệm
- **_VCS_** là hệ thống kiểm soát các phiên bản phân tán mã nguồn mở. Các VCS lưu trữ tất cả các file, ghi lại toàn bộ lịch sử thay đổi của file. Mỗi sự thay đổi được lưu lại sẽ được và thành một **_Ver_**.

- VCS giúp lập trình viên lưu trữ nhiều phiên bản khác nhau của 1 mã nguồn được **Clone** từ 1 **_Repo_**, mỗi thay đổi vào mã nguồn trên local sẽ có thể **Commit** rồi đưa lên server nơi đặt **_Repo_** chính.
  
- 1 máy tính khác nếu họ có quyền truy cập cũng có thể **Clone** lại mã nguồn từ kho chứa / **Clone** lại một tập hợp các thay đổi mới nhất trên máy tính kia.

- Lập trình viên có thể xem **Timeline** các thay đổi của dự án, mỗi **_Ver_** lưu lại:
	- **Nội dung thay đổi**
	- **Thời gian chỉnh sửa**
	- **Người thực hiện**
	- **Lý do / mô tả**

---

## 2. Tác dụng
1. Lưu lịch sử các **_Ver_** của bất kỳ thay đổi. Giúp xem lại các sự thay đổi /  **_Rev_** lại sau này.
2. Việc chia sẻ code trở nên dễ dàng hơn, lập trình viên có thể để public / private.