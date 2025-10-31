## 0. Thuật ngữ
### 0.1. Chính
1. **Distributed Version Control System _– DVCS_:** Hệ thống quản lý phiên bản phân tán
2. **Repository - _Repo_:** Kho lưu trữ
3. **Version Control System - _VCS_:** Hệ thống quản lý phiên bản phân tán mã nguồn mở → [Xem tại đây](Version%20Control%20System)
4. **Differential changes:** Danh sách thay đổi
5. **Snapshot:** Ảnh chụp
6. **Commit:** Ủy thác
7. **Deployment -  _Deploy_:** Triển khai
8. **Clone:** Nhân bản
9. **Revert - _Rev_:** Khôi phục
10. **Branching:** Phân nhánh
### 0.2. Cơ bản
- **Branch**: Nhánh tách ra từ project chính, cho phép thử nghiệm hoặc phát triển song song và có thể quay lại phiên bản cũ.  
- **Commit**: Một mốc thời gian (snapshot) lưu lại thay đổi trong dự án. Được tạo sau khi `git add`.  
- **Checkout**: Lệnh chuyển đổi giữa các branch (`git checkout <branch>` / `git checkout master`).  
- **Fetch**: Lấy về dữ liệu branch mới nhất từ remote, nhưng chưa merge vào local.  
- **Fork**: Bản sao của repository, dùng để phát triển/ thử nghiệm độc lập mà không ảnh hưởng đến repo gốc.  
- **Head**: Commit mới nhất của một branch.  
- **Index (Staging area)**: Khu vực tạm chứa các thay đổi trước khi commit. Kiểm tra bằng `git status`. 
- **Master/Main**: Nhánh chính (mặc định) của repository, thường chứa code ổn định nhất. 
	![[Thuat_ngu-Master.png]]
- **Merge**: Gộp thay đổi từ một branch khác vào branch hiện tại.  
- **Origin**: Tên mặc định của remote repository. Thường dùng trong lệnh `git push origin master`.  
	![[Thuat_ngu-Origin.png]]
- **Pull**: Kết hợp thay đổi từ remote vào local (`git pull`). Trong team, còn có **Pull Request** để đề xuất merge.  
- **Push**: Đẩy commit từ local repository lên remote (`git push`).  
- **Rebase**: Sắp xếp lại lịch sử commit, cho phép dời/ghép commit từ branch này sang branch khác.  
- **Remote**: Repository nằm trên server (GitHub, GitLab, Bitbucket...) để đồng bộ với repo local.  
- **Repository (Repo)**: Kho chứa toàn bộ dự án, gồm **file, branch, commit, tag...**  
- **Stash**: Lưu tạm các thay đổi chưa commit để chuyển sang việc khác, sau có thể lấy lại (`git stash`).  
- **Tag**: Dùng để đánh dấu commit quan trọng (ví dụ: release version).  
- **Upstream**: Nhánh gốc mà local branch theo dõi và push/pull dữ liệu về (thường là `main` hoặc `master`).  
- **Mở rộng** → [Git docs reference](https://git-scm.com/docs)

---

## 1. Khái niệm:
- `Git` là một **_DVCS_** phổ biến nhất hiện nay. 
- `Git` cung cấp cho mỗi lập trình viên **_Repo_** riêng chứa toàn bộ lịch sử thay đổi.

---

## 2. Tác dụng
- Vốn là 1 VCS nên Git cũng ghi nhớ lại toàn bộ lịch sử thay đổi của mã nguồn.
- Lập trình sửa file, thêm dòng code tại đâu, xóa dòng code ở hàng nào…đều được Git ghi nhận và lưu trữ lại.

--- 

## 3. Hoạt động
| Tiêu chí             | CVS, Subversion, Perforce, Bazaar...                   | Git                                                    |
| -------------------- | ------------------------------------------------------ | ------------------------------------------------------ |
| Cách lưu dữ liệu     | Lưu **Differential changes** theo file  theo thời gian | Lưu **Snapshot** toàn bộ dự án tại mỗi **Commit**      |
| Xử lý file không đổi | Vẫn ghi lại thông tin theo từng lần thay đổi           | Không lưu lại file → chỉ tạo liên kết tới phiên bản cũ |
| Cách nhìn dữ liệu    | Tập hợp file + các thay đổi của từng file              | Bộ sưu tập các **Snapshot** của toàn dự án             |
| Bản chất             | Đơn thuần, tiếp nối thế hệ trước                       | 1 hệ thống file thu nhỏ, công cụ quản lý mạnh mẽ       |
| Minh hoạ             | ![[Hoat_dong-0.png]]                                   | ![[Hoat_dong-1.png]]                                   |

---

## 4. Lợi ích
- Hỗ trợ nhiều lập trình viên làm việc song song → tránh xung đột code
- Dễ dàng **_Rev_** khi cần
- Cho phép phát triển song song nhờ **branching**
- Nhanh, gọn, an toàn, dễ thao tác
- **Clone _Repo_** & làm việc ở bất cứ đâu
- **_Deploy_** sản phẩm đơn giản hơn

---

## 5. Các lệnh cơ bản
### 5.1. git config
- Tác dụng : Để set user name và email của bạn trong main configuration file.  
- Cách xài : 
	- Để kiểm tra tên và kiểu email trong cấu hình dùng _**`git config -- globaluser.name`**_ và _**`git config -- global user.email`**_.
	- Để set email hoặc tên mới _**`git config -- global user.name = “Hải Nguyễn”`**_ và _**`git config -- global user.email =“hainguyen@gmail.com”`**_

### 5.2. git init
- Tác dụng : Khởi tạo 1 git repository 1 project mới hoặc đã có.
- Cách xài: **_`git init`_** trong thư mục gốc của dự án.

### 5.3. git clone
- Tác dụng: Copy 1 git repository từ remote source.
- Cách xài: **_`git clone <:clone git url:>`_**

#### 5.4. git status
- Tác dụng: Để check trạng thái của những file bạn đã thay đổi trong thư mục làm việc. VD: Tất cả các thay đổi cuối cùng từ lần commit cuối cùng.
- Cách xài: **_`git status`_** trong thư mục làm việc.

#### 5.5. git add
- Tác dụng: Thêm thay đổi đến stage/index trong thư mục làm việc.
- Cách xài: **_`git add`_**

### 5.6. git commit
- Tác dụng:
	- Commit nghĩa là một action để Git lưu lại một snapshot của các sự thay đổi trong thư mục làm việc. Và các tập tin, thư mục được thay đổi đã phải nằm trong Staging Area.
	- Mỗi lần commit nó sẽ được lưu lại lịch sử chỉnh sửa của code kèm theo tên và địa chỉ email của người commit. 
	- Ngoài ra trong Git bạn cũng có thể khôi phục lại tập tin trong lịch sử commit của nó để chia cho một branch khác, vì vậy bạn sẽ dễ dàng khôi phục lại các thay đổi trước đó.
- Cách dùng: **_`git commit -m ”Đây là message, bạn dùng để note những thay đổi để sau này dễ dò lại”`_**

### 5.7. git push/git pull
- Tác dụng: Push hoặc Pull các thay đổi đến remote. Nếu bạn đã added và committed các thay đổi và bạn muốn đẩy nó lên hoặc remote của bạn đã update và bạn apply tất cả thay đổi đó trên code của mình.
- Cách dùng: **_`git pull <:remote:> <:branch:>`_** và **_`git push <:remote:> <:branch:>`_**

#### 5.8. git branch
- Tác dụng: liệt kê tất cả các branch (nhánh).
- Cách dùng: **_`git branch`_** hoặc **_`git branch -a`_**

### 5.9. git checkout
- Tác dụng: Chuyển sang branch khác
- Cách dùng: **_`git checkout <: branch:>`_** hoặc **_`git checkout -b <: branch:>`_** nếu bạn muốn tạo và chuyển sang một chi nhánh mới.

### 5.10. git stash
- Tác dụng: Lưu thay đổi mà bạn không muốn commit ngay lập tức.
- Cách dùng: **_`git stash`_** trong thư mục làm việc của bạn.

### 5.11. git merge
- Tác dụng: Merge 2 branch lại với nhau.
- Cách dùng: Chuyển tới branch bạn muốn merge rồi  dùng **_`git merge <:branch_ban_muon_merge:>`_**

### 5.12. git reset
- Tác dụng: Bạn đã đưa một tập tin nào đó vào Staging Area nhưng bây giờ bạn muốn loại bỏ nó ra khỏi đây để không phải bị commit theo.
- Cách dùng: **_`git reset HEAD tên_file`_**

### 5.13. git remote
- Tác dụng: Để check remote/source bạn có hoặc add thêm remote
- Cách dùng: **_`git remote`_** để kiểm tra và liệt kê. Và **_`git remote add <: remote_url:>`_** để thêm.

#### 5.14. git add
- Tác dụng: Để đưa một tập tin vào Staging Area
- Cách dùng: **_`git add tên_file`_** hoặc muốn thêm hết file của thư mục thì **_`git add all`_**

--- 

## 6. Lời khuyên
- Git Cheat Sheets: Tham khảo nhanh khi quên lệnh: 
	- [Git Guide](https://rogerdudler.github.io/git-guide/) 
	- [Git Official Tutorial](https://git-scm.com/docs/gittutorial) 
	- [GitSheet](https://gitsheet.wtf/) 
	- [Interactive Cheatsheet](http://ndpsoftware.com/git-cheatsheet.html) 
	- [Git Explorer](https://gitexplorer.com/) 

- Commit thường xuyên: Chia nhỏ commit, commit đều đặn để dễ tích hợp code và hạn chế xung đột. 

- Test trước khi commit: Chỉ commit khi thay đổi đã được test và đảm bảo hoạt động. 

- Viết message rõ ràng: Ghi chú chi tiết thay đổi để đồng đội dễ theo dõi. 

- Tận dụng branch: Dùng branch để thử nghiệm hoặc phát triển song song. 

- Theo Git Workflow chung: Cả team nên thống nhất một workflow (Git Flow, Feature Branch...) để phối hợp hiệu quả.

	![[Loi_khuyen-Git_workflow.png]]