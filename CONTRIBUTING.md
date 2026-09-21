# Hướng dẫn đóng góp

Tài liệu này áp dụng cho toàn bộ các kho (repository) của tổ chức `vba-org`.

Nếu bạn chưa quen GitHub, hãy đọc mục **Thuật ngữ cần biết** trước — toàn bộ quy trình bên dưới chỉ xoay quanh 6 khái niệm: *issue → branch → commit → pull request → review → merge*.

---

## 1. Thuật ngữ cần biết

GitHub dùng nguyên các từ tiếng Anh trong giao diện, nên tài liệu này giữ nguyên từ gốc và giải thích bên cạnh.

### 1.1. Nơi lưu trữ

| Thuật ngữ | Cách gọi tiếng Việt | Giải thích |
|---|---|---|
| **Repository** (viết tắt **repo**) | Kho | Nơi chứa toàn bộ tệp của một dự án **cùng với lịch sử mọi lần sửa**. Mỗi kho có một địa chỉ riêng, ví dụ `github.com/vba-org/handbook`. |
| **Organization** (**org**) | Tổ chức | Tài khoản chung của Hiệp hội trên GitHub (`vba-org`), sở hữu nhiều kho và quản lý quyền truy cập của thành viên. |
| **Clone** | Sao về máy | Tải một bản sao đầy đủ của kho xuống máy tính để làm việc ngoại tuyến. |
| **Fork** | Tách bản riêng | Tạo một bản sao của kho sang tài khoản cá nhân. Dùng khi bạn **không có quyền ghi** trực tiếp vào kho gốc. |

### 1.2. Sáu khái niệm cốt lõi của quy trình

| Thuật ngữ | Cách gọi tiếng Việt | Giải thích |
|---|---|---|
| **Issue** | Phiếu việc / phiếu vấn đề | Một bài đăng trong kho để nêu **một việc cần làm**: báo lỗi, đề xuất nội dung mới, hoặc đặt câu hỏi. Mỗi issue có số thứ tự (`#12`), người phụ trách, nhãn phân loại, và trạng thái *Open* (đang mở) hoặc *Closed* (đã đóng). Issue là nơi **thảo luận trước khi làm**, không phải nơi chứa tệp. |
| **Branch** | Nhánh | Một "bản làm việc song song" của kho. Bạn tách nhánh ra, sửa thoải mái trên đó, mà **bản chính vẫn nguyên vẹn** cho tới khi thay đổi được duyệt. Hình dung như photocopy một chương tài liệu ra sửa nháp, thay vì viết đè lên bản gốc. |
| **Commit** | Lần lưu thay đổi | Một lần "chốt" các sửa đổi kèm dòng mô tả ngắn giải thích **đã sửa gì**. Đây là đơn vị nhỏ nhất của lịch sử: mỗi commit đều có thể xem lại, so sánh, hoặc quay ngược. Một lần sửa nhỏ = một commit; đừng dồn cả chục việc khác nhau vào một commit. |
| **Pull request** (viết tắt **PR**) | Đề nghị gộp | Yêu cầu chính thức: *"tôi đã sửa xong trên nhánh của mình, xin gộp vào bản chính"*. PR hiển thị toàn bộ khác biệt trước/sau và mở một luồng thảo luận để mọi người góp ý từng dòng. |
| **Review / Approve** | Rà soát / Phê duyệt | Người khác đọc PR rồi chọn: *Approve* (đồng ý), *Request changes* (yêu cầu sửa), hoặc *Comment* (góp ý). Tại `vba-org`, **cần tối thiểu 1 phê duyệt** thì PR mới được gộp. |
| **Merge** | Gộp | Thao tác cuối: đưa thay đổi từ nhánh làm việc vào nhánh chính. Sau khi merge, nội dung mới chính thức trở thành bản chuẩn. |

### 1.3. Đặt tên và phiên bản

| Thuật ngữ | Cách gọi tiếng Việt | Giải thích |
|---|---|---|
| **Branch chính** (`main`) | Nhánh chính | Nhánh gốc của kho, luôn chứa **phiên bản đã duyệt và dùng được**. Không ai sửa trực tiếp lên `main`; mọi thay đổi phải đi qua pull request. |
| **Branch làm việc** | Nhánh làm việc | Nhánh tạm, tách ra từ `main` để làm **một việc cụ thể** (thường ứng với một issue). Xóa sau khi đã merge. Tên đặt theo dạng `loai/mo-ta-ngan`, ví dụ `docs/handbook-ch3`. |
| **Conventional Commits** | Quy ước viết mô tả commit | Chuẩn quốc tế về cách viết dòng mô tả: `loai(pham-vi): mo ta ngan`. Các `loai` hay dùng: `feat` (thêm mới), `fix` (sửa lỗi), `docs` (tài liệu), `refactor` (sắp xếp lại, không đổi nội dung), `chore` (việc vặt). Ví dụ: `docs(glossary): them thuat ngu stablecoin`. |
| **Tag** | Thẻ phiên bản | Nhãn gắn cố định vào một thời điểm trong lịch sử để đánh dấu **một phiên bản phát hành**. Khác với branch (luôn chạy tiếp), tag đứng yên vĩnh viễn — dùng để trích dẫn đúng bản tài liệu tại một mốc. |
| **SemVer** (Semantic Versioning) | Đánh số phiên bản ngữ nghĩa | Quy ước `vMAJOR.MINOR.PATCH`, ví dụ `v1.2.0`: tăng **MAJOR** khi thay đổi lớn phá vỡ tương thích, **MINOR** khi thêm nội dung mới, **PATCH** khi chỉ sửa lỗi nhỏ. |
| **Release** | Bản phát hành | Gói công bố gắn với một tag, kèm ghi chú thay đổi và tệp đính kèm (PDF, bản in…). |

---

## 2. Quy trình

1. **Tạo issue** mô tả vấn đề hoặc đề xuất **trước khi bắt tay vào làm**.
   → Mục đích: để mọi người biết việc đang có người nhận, tránh hai người làm trùng, và thống nhất hướng xử lý trước khi tốn công.

2. **Tạo branch** theo quy ước: `feat/`, `fix/`, `docs/`.
   → Tách nhánh từ `main`. Mọi chỉnh sửa diễn ra trên nhánh này, `main` không bị ảnh hưởng.

3. **Commit** từng thay đổi kèm mô tả rõ ràng.
   → Chia nhỏ theo từng việc để người rà soát dễ theo dõi.

4. **Gửi pull request**, liên kết tới issue tương ứng.
   → Ghi `Closes #12` trong phần mô tả PR: khi PR được merge, issue số 12 sẽ tự động đóng.

5. **Chờ rà soát.** Cần **tối thiểu 1 phê duyệt (approve)** trước khi merge vào `main`.
   → Nếu người rà soát chọn *Request changes*, hãy sửa và commit tiếp lên đúng nhánh đó — PR tự cập nhật, không cần tạo PR mới.

6. **Merge** vào `main`, sau đó xóa nhánh làm việc.

---

## 3. Quy ước đặt tên

| Đối tượng | Quy ước | Ví dụ |
|---|---|---|
| Branch chính (nhánh chính) | `main` | `main` |
| Branch làm việc (nhánh làm việc) | `loai/mo-ta-ngan` | `docs/handbook-ch3` |
| Commit (lần lưu thay đổi) | Conventional Commits, tiếng Anh không dấu | `docs(glossary): them thuat ngu stablecoin` |
| Tag (thẻ phiên bản) | SemVer cho phần mềm, `YYYY.MM` cho tài liệu | `v1.2.0` · `2026.09` |

**Vì sao commit viết tiếng Anh không dấu:** để tránh lỗi hiển thị font và lỗi mã hóa trên các công cụ dòng lệnh, đồng thời thống nhất với chuẩn Conventional Commits. Riêng **nội dung tài liệu** vẫn viết tiếng Việt có dấu đầy đủ.

---

## 4. Nguyên tắc nội dung

- Viết tiếng Việt có dấu, văn phong trung lập.
- Mọi số liệu và viện dẫn pháp lý phải ghi nguồn và thời điểm, dùng đầy đủ ký hiệu văn bản (ví dụ: Nghị định số 30/2020/NĐ-CP).
- Không đưa khuyến nghị đầu tư vào tài liệu của Hiệp hội.
- Không phát ngôn nhân danh Hiệp hội nếu chưa được phân công.

---

## 5. Phạm vi

Nội dung trong các kho này là thông tin tham khảo, không phải tư vấn pháp lý hay tư vấn đầu tư.
