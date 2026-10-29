# BÀI LÀM: TỔ CHỨC CLOUD WORKSPACE CHO DỰ ÁN SMARTCAMPUS

## PHẦN 1 – THIẾT LẬP HYBRID WORKFLOW

### 1. Xử lý sự cố laptop hỏng ổ cứng

Nếu nhóm đã thiết lập đúng **Hybrid Workflow (Local + Auto Sync)** từ đầu và file đã đồng bộ thành công lên Cloud trước khi ổ cứng hỏng, nhóm vẫn có thể khôi phục bản mới nhất từ Cloud.

**Lý do:** File được lưu trên máy tính cục bộ và tự động đồng bộ lên Cloud. Khi laptop gặp sự cố, thành viên có thể đăng nhập trên thiết bị khác để tải lại file.

**Lưu ý:** Nếu file chưa kịp đồng bộ hoặc đang có lỗi đồng bộ, bản mới nhất có thể chưa được lưu trên Cloud.

### 2. Ba bước thiết lập Auto Sync

1. **Cài đặt:** Cài ứng dụng Google Drive for desktop và đăng nhập tài khoản Google của nhóm.
2. **Thiết lập đồng bộ:** Chọn thư mục dự án SmartCampus trên máy tính để đồng bộ với Google Drive, bảo đảm file được lưu trên Cloud.
3. **Kiểm tra:** Tạo hoặc sửa một file thử nghiệm, xác nhận file xuất hiện trên Google Drive và trạng thái đồng bộ đã hoàn tất.

### 3. Khôi phục hai trang bị xóa nhầm

Sử dụng tính năng **Version History (Lịch sử phiên bản)**:

1. Mở file `BaoCao_CuoiKy_SmartCampus.docx` trên Google Drive hoặc Google Docs.
2. Chọn **File → Version history → See version history**.
3. Chọn phiên bản trước thời điểm xóa nhầm.
4. Nhấn **Restore this version** để khôi phục phiên bản đó.

Nếu chỉ muốn lấy lại hai trang đã xóa mà vẫn giữ các chỉnh sửa mới khác, hãy sao chép phần nội dung từ phiên bản cũ sang phiên bản hiện tại.

### 4. Hai sai lầm khi đồng bộ dữ liệu lên Cloud

* **Đồng bộ thư mục `node_modules`:** Chứa hàng vạn file nhỏ, làm tăng tải đồng bộ, tiêu tốn tài nguyên và có thể gây xung đột. Cách xử lý: loại thư mục này khỏi đồng bộ và sử dụng tệp quản lý phụ thuộc để cài đặt lại khi cần.
* **Đồng bộ các file phim 4K không phục vụ dự án:** Chiếm nhiều dung lượng Cloud và băng thông không cần thiết. Cách xử lý: lưu ở ổ đĩa cá nhân hoặc nơi lưu trữ giải trí riêng, không đưa vào thư mục dự án.

---

## PHẦN 2 – PHÂN QUYỀN CHIA SẺ AN TOÀN

### 1. Bảng phân quyền cho từng file

| File                             | Mức quyền                      | Phạm vi chia sẻ                                        | Giải thích                                                                                          |
| -------------------------------- | ------------------------------ | ------------------------------------------------------ | --------------------------------------------------------------------------------------------------- |
| `BaoCao_CuoiKy_SmartCampus.docx` | Viewer                         | Restricted – tài khoản giảng viên                      | Giảng viên chỉ cần xem và chấm điểm, không cần chỉnh sửa trực tiếp.                                 |
| `Slide_BaoCao.pptx`              | Editor                         | Restricted – 5 thành viên nhóm                         | Cả 5 người cần cùng chỉnh sửa trong hai ngày cuối, nhưng chỉ thành viên nhóm được truy cập.         |
| `GopY_BanNhap.docx`              | Commenter                      | Restricted – tài khoản anh khóa trên                   | Anh khóa trên có thể nhận xét, góp ý mà không sửa trực tiếp nội dung.                               |
| `ThongTin_CaNhan_NhomVien.xlsx`  | Viewer hoặc Editor tùy nhu cầu | Restricted – chỉ tài khoản được ủy quyền xử lý thủ tục | Chỉ người thực sự cần sử dụng thông tin CCCD và SĐT mới được cấp quyền; không chia sẻ ra bên ngoài. |

**Lưu ý:** Với file thông tin cá nhân, chỉ chọn một mức quyền phù hợp với nhiệm vụ thực tế. Nếu người xử lý chỉ cần xem thông tin, chọn `Viewer`; nếu cần cập nhật dữ liệu, cấp `Editor` cho đúng người được ủy quyền.

### 2. Quy tắc Cờ Đỏ Bảo mật

**Quy tắc Cờ Đỏ:** Tài liệu chứa thông tin cá nhân hoặc dữ liệu nhạy cảm phải được đặt ở chế độ `Restricted` và chỉ chia sẻ cho tài khoản được ủy quyền.

Không được kết hợp `Anyone with the link` + `Editor` đối với `ThongTin_CaNhan_NhomVien.xlsx`, vì:

* Bất kỳ ai có liên kết đều có thể truy cập mà không cần được cấp quyền riêng theo danh tính.
* Người có quyền Editor có thể sửa hoặc xóa dữ liệu CCCD, SĐT.
* Liên kết bị chuyển tiếp có thể làm lộ thông tin cá nhân và gây rủi ro bảo mật.

### 3. Hai thao tác trong cửa sổ Settings cho Slide_BaoCao.pptx

Trong phần **Share → Settings** của Google Drive, thực hiện:

1. **Tắt `Editors can change permissions and share`** để hạn chế Editor tự thay đổi quyền hoặc mời người ngoài vào tài liệu.
2. **Bật hoặc tắt tùy chọn `Viewers and commenters can see the option to download, print, and copy` tùy nhu cầu bảo mật.** Nếu cần hạn chế tải xuống, in và sao chép, hãy tắt tùy chọn này.

Đối với `Slide_BaoCao.pptx`, nên tắt quyền Editor tự thay đổi quyền chia sẻ. Tùy chọn tải xuống nên được quyết định theo nhu cầu sử dụng của nhóm; không nên hạn chế nếu các thành viên cần tải bản trình chiếu để làm việc offline.

---

## PHẦN 3 – TỔ CHỨC GIAO TIẾP NHÓM CHUẨN DOANH NGHIỆP

### 1. Ba vấn đề trong hội thoại Zalo

1. **No-Hello:** Lan chỉ nhắn “có ai rảnh không” rồi chờ phản hồi, không nêu rõ công việc cần hỗ trợ.
2. **Notification Pollution:** Trưởng nhóm sử dụng `@all` lúc 23:47, gây phiền cho cả nhóm vào giờ nghỉ và làm giảm hiệu quả thông báo.
3. **Thiếu phân luồng và ngữ cảnh:** Tin nhắn công việc, ảnh mèo và trò chuyện giải trí nằm chung một luồng, khiến thông tin quan trọng dễ bị trôi.

### 2. Đề xuất Channel/Topic

* `#thong-bao`: Thông báo deadline, phân công và tiến độ quan trọng.
* `#bao-cao-do-an`: Trao đổi nội dung báo cáo, slide và chỉnh sửa tài liệu.
* `#hoi-dap-ho-tro`: Đặt câu hỏi và hỗ trợ kỹ thuật.
* `#tam-su-giai-tri`: Trò chuyện ngoài công việc.

### 3. Viết lại tin nhắn của Lan theo tư duy Asynchronous

> Chào mọi người, mình đang hoàn thiện phần giao diện trong báo cáo SmartCampus và chưa rõ cách trình bày sơ đồ chức năng ở mục 2.3. Khi có thời gian, mọi người góp ý giúp mình nên dùng sơ đồ luồng hay sơ đồ khối nhé. Mình sẽ tiếp tục hoàn thiện các phần còn lại trong lúc chờ phản hồi. Cảm ơn mọi người!

Tin nhắn có đủ bối cảnh, câu hỏi cụ thể và không yêu cầu người nhận phải trả lời ngay lập tức.

### 4. Viết lại tin nhắn bằng Schedule Send

**Thiết lập:** Soạn tin nhắn lúc 23:47 và sử dụng **Schedule Send** để gửi lúc **08:00 sáng hôm sau**.

> Chào Nam và Hoa, hiện phần kiểm thử API và phần tổng hợp kết quả trong báo cáo SmartCampus vẫn chưa được xác nhận hoàn tất. Nam vui lòng cập nhật tiến độ kiểm thử API; Hoa vui lòng hoàn thiện phần tổng hợp kết quả trước 10:00 sáng nay. Nếu có vướng mắc, hai bạn phản hồi tại đây để nhóm cùng xử lý. Cảm ơn mọi người!


---

## PHẦN 4 – THÔNG BÁO TỔNG HỢP

### Tin nhắn đăng lên kênh `#thong-bao`

> Chào mọi người, mình đã thiết lập Auto Sync cho thư mục dự án SmartCampus trên Google Drive và kiểm tra trạng thái đồng bộ. Từ giờ, mọi người hãy làm việc trong thư mục dự án đã đồng bộ để hạn chế thất lạc phiên bản; riêng `node_modules` và các file phim 4K không cần thiết sẽ không đưa vào đồng bộ. Mình cũng đã chia sẻ `BaoCao_CuoiKy_SmartCampus.docx` cho giảng viên với quyền **Viewer** và phạm vi **Restricted**, đồng thời thiết lập quyền **Editor** cho 5 thành viên đối với `Slide_BaoCao.pptx`. Nam vui lòng cập nhật phần kiểm thử API, Hoa vui lòng hoàn thiện phần tổng hợp kết quả trước 10:00 sáng nay. Nếu có vướng mắc, hai bạn phản hồi tại kênh `#bao-cao-do-an` để nhóm xử lý kịp deadline. Cảm ơn mọi người!

