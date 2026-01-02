## Thuật ngữ
### Thuật ngữ Hệ thống
| Thuật ngữ                              | Viết tắt   | Ý nghĩa                                                  | Đường dẫn                                 |
| :------------------------------------- | :--------- | :------------------------------------------------------- | ----------------------------------------- |
| **Distributed Version Control System** | **DVCS**   | Hệ thống quản lý phiên bản phân tán                      |                                           |
| **Repository**                         | **Repo**   | Kho lưu trữ toàn bộ dự án (file, branch, commit, tag...) |                                           |
| **Version Control System**             | **VCS**    | Hệ thống quản lý phiên bản mã nguồn mở                   | [Xem tại đây](Version%20Control%20System) |
| **Differential changes**               |            | Danh sách các thay đổi giữa các phiên bản                |                                           |
| **Snapshot**                           |            | Ảnh chụp toàn bộ trạng thái dự án tại một thời điểm      |                                           |
| **Commit**                             |            | Hành động ủy thác/lưu lại snapshot vào lịch sử           |                                           |
| **Deployment**                         | **Deploy** | Triển khai sản phẩm lên môi trường thực tế               |                                           |
| **Clone**                              |            | Nhân bản một repository từ remote về local               |                                           |
| **Revert**                             | **Rev**    | Khôi phục lại trạng thái cũ của mã nguồn                 |                                           |
| **Branching**                          |            | Cơ chế phân nhánh phát triển song song                   |                                           |

### Thuật ngữ Thao tác & Thành phần
| Thuật ngữ           | Chi tiết khái niệm                                                           | Minh hoạ                  | Đường dẫn                               |
| :------------------ | :--------------------------------------------------------------------------- | ------------------------- | --------------------------------------- |
| **Branch**          | Nhánh tách ra từ dự án chính để thử nghiệm hoặc phát triển tính năng mới     |                           |                                         |
| **Checkout**        | Lệnh chuyển đổi giữa các branch hoặc quay lại một commit cũ                  |                           |                                         |
| **Fetch**           | Lấy dữ liệu mới nhất từ Remote về nhưng **chưa merge** vào local             |                           |                                         |
| **Fork**            | Bản sao của một repo, dùng để phát triển độc lập mà không ảnh hưởng repo gốc |                           |                                         |
| **Head**            | Con trỏ chỉ định commit mới nhất của branch hiện tại                         |                           |                                         |
| **Index (Staging)** | Khu vực tạm chứa các thay đổi trước khi commit. Kiểm tra bằng `git status`   |                           |                                         |
| **Master/Main**     | Nhánh chính (mặc định), thường chứa mã nguồn ổn định nhất                    | ![[Thuat_ngu-Master.png]] |                                         |
| **Merge**           | Gộp thay đổi từ một branch khác vào branch hiện tại                          |                           |                                         |
| **Origin**          | Tên mặc định của remote repository (server)                                  | ![[Thuat_ngu-Origin.png]] |                                         |
| **Pull**            | Kết hợp: Tải dữ liệu từ remote và gộp ngay vào local (`git pull`)            |                           |                                         |
| **Push**            | Đẩy các commit từ máy cá nhân lên server                                     |                           |                                         |
| **Rebase**          | Sắp xếp lại lịch sử commit, giúp sơ đồ nhánh trông thẳng và sạch hơn         |                           |                                         |
| **Remote**          | Repo nằm trên server (GitHub, GitLab, Bitbucket...)                          |                           |                                         |
| **Stash**           | Lưu tạm các thay đổi chưa commit vào "ngăn kéo" để chuyển việc khác          |                           |                                         |
| **Tag**             | Đánh dấu các commit quan trọng (thường là các bản release version)           |                           |                                         |
| **Upstream**        | Nhánh gốc mà local branch đang theo dõi để push/pull                         |                           |                                         |
| **Mở rộng**         |                                                                              |                           | [Xem tại đây](https://git-scm.com/docs) |

## Tổng quan về Git

> [!ABSTRACT] Khái niệm
> **Git** là một **DVCS** phổ biến nhất hiện nay. Nó cung cấp cho mỗi lập trình viên một **Repo** riêng chứa toàn bộ lịch sử thay đổi, giúp làm việc offline và độc lập hiệu quả

### So sánh Git & VCS truyền thống

| Tiêu chí           | SVN, Perforce...                              | Git                                                  |
| :----------------- | :-------------------------------------------- | :--------------------------------------------------- |
| **Lưu dữ liệu**    | Lưu **Differential changes** (biến động file) | Lưu **Snapshot** (ảnh chụp toàn bộ dự án)            |
| **File không đổi** | Ghi lại thông tin theo từng lần thay đổi      | Chỉ tạo liên kết tới phiên bản cũ (tiết kiệm bộ nhớ) |
| **Cách nhìn**      | Tập hợp file + các thay đổi nhỏ lẻ            | Bộ sưu tập các Snapshot nối tiếp nhau                |
| **Bản chất**       | Tiếp nối thế hệ trước, phụ thuộc server       | Một hệ thống file thu nhỏ, quản lý mạnh mẽ           |
| **Minh hoạ**       | ![[Hoat_dong-0.png]]                          | ![[Hoat_dong-1.png]]                                 |

## Các lệnh cơ bản

### Cấu hình & Khởi tạo
- `git config --global user.name "Tên của bạn"`: Thiết lập tên định danh
- `git config --global user.email "email@example.com"`: Thiết lập email định danh
- `git init`: Biến thư mục hiện tại thành một Git Repository
- `git clone <url>`: Tải một dự án có sẵn từ server về máy

### Làm việc với thay đổi
- `git status`: Kiểm tra trạng thái các file (đã sửa, đã add hay chưa)
- `git add <tên_file>`: Đưa file vào **Staging Area**. Dùng `git add .` để thêm tất cả
- `git commit -m "Thông điệp"`: Lưu snapshot các file trong Staging Area vào lịch sử
- `git reset HEAD <file>`: Loại bỏ file khỏi Staging Area (hủy add)

### Nhánh & Đồng bộ
- `git branch`: Liệt kê các nhánh đang có
- `git checkout <tên_nhánh>`: Chuyển sang nhánh khác
- `git checkout -b <tên_nhánh>`: Tạo mới và chuyển sang nhánh đó ngay lập tức
- `git merge <tên_nhánh>`: Gộp nhánh chỉ định vào nhánh hiện tại
- `git push origin <tên_nhánh>`: Đẩy code lên server
- `git pull origin <tên_nhánh>`: Lấy code từ server về máy
- `git stash`: Tạm cất code đang làm dở

## Lời khuyên & Quy trình

> [!SUCCESS] Quy tắc vàng
> 1. **Commit thường xuyên**: Chia nhỏ công việc thành các commit có ý nghĩa
> 2. **Test trước khi commit**: Đảm bảo code không làm hỏng dự án
> 3. **Viết message rõ ràng**: Giúp đồng đội (và chính bạn sau này) hiểu đã sửa gì
> 4. **Tận dụng Branch**: Tuyệt đối không code tính năng mới trực tiếp trên `main/master`
> ![[Loi_khuyen-Git_workflow.png]]

### Tài liệu tham khảo nhanh
- [Git Explorer](https://gitexplorer.com/) - Tìm lệnh theo nhu cầu thực tế
- [Git Official Tutorial](https://git-scm.com/docs/gittutorial) , [Git Guide](https://rogerdudler.github.io/git-guide/) - Hướng dẫn trực quan
- [Interactive Cheatsheet](http://ndpsoftware.com/git-cheatsheet.html),  [GitSheet](https://gitsheet.wtf/) - Bản đồ các khu vực trong Git