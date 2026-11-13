# Thiết kế hệ thống website — Trung tâm đào tạo (Công ty TNHH Đào tạo Đắc Thành)

Ngày chốt: 2026-11-13. Tài liệu này ghi lại mô hình vận hành đã xác nhận và thiết kế hệ thống.

## 1. Mô hình vận hành đã xác nhận

- Tên trên website: **Công ty TNHH Đào tạo Đắc Thành**.
- 18 lớp, khoảng 320 học sinh, khối 6–12, môn Toán / Văn / Anh văn (gồm lớp chuyên).
- Giáo viên: Nguyễn Chí Trung (10 lớp Toán), Đoàn Thị Hải Lý (2 lớp Văn 9), Nguyễn Tuấn Anh (3 lớp Anh chuyên), Nguyễn Thị Thanh Tâm (3 lớp Anh văn tự mở).
- Hai mô hình lớp:
  - **Lớp tự mở** (3 lớp, cô Tâm): trung tâm thu toàn bộ học phí, trả lương giáo viên.
  - **Lớp liên kết** (15 lớp): giáo viên mở lớp; trung tâm thu phí quản lý **10%** (thầy Trung, cô Hải Lý) hoặc **12,5%** (thầy Tuấn Anh) trên tổng học phí, cộng tiền phòng và lương trợ giảng; giáo viên đóng phần còn thiếu hoặc được hoàn lại, số dư chuyển tháng sau.
- Công thức "giáo viên cần đóng": học phí × học sinh × buổi − phí quản lý − tiền phòng − lương giáo viên − lương trợ giảng.
- Không có tạm ứng cho giáo viên.
- Học phí: **300.000đ/buổi** (Anh văn 9 chuyên C: 375.000đ/buổi). Lương giáo viên 1.000.000–2.000.000đ/buổi. Lương trợ giảng 375.000đ/buổi.
- Học sinh được đóng học phí nhiều tháng. Học sinh đóng một lúc nhiều buổi nhưng mỗi tháng chỉ học 4–5 buổi, nên phần còn lại được phân bổ vào các tháng sau.
- Nghỉ do trung tâm: tháng đó giảm buổi nghỉ. Học sinh tự nghỉ: chỉ ghi nhận có phép hay không phép, buổi đó vẫn tính tiền.
- Bảo lưu: doanh thu chỉ tính đến lúc học sinh dừng học để bảo lưu, phần còn lại không phải doanh thu công ty.
- Hoàn học phí: trước buổi đầu của tháng hoàn 100% học phí đã đóng; đã dùng 1–2 buổi hoàn 50% phần học phí còn lại của tháng; đã dùng từ 3 buổi trở lên không hoàn tháng đó. Phần còn lại sau hoàn là doanh thu công ty.
- Người dùng website: nhân sự bộ phận, quản lý bộ phận, giáo viên, trợ giảng. Có phần điểm danh học sinh. Phụ huynh/học sinh không cần tài khoản.

## 2. Phòng học và nghiệm thu phòng

- Phòng: Hội trường (2 mức giá 1.100.000đ và 800.000đ — giá phòng set up theo từng lớp; trong 1 tháng một lớp có thể dùng nhiều loại phòng với đơn giá khác nhau), Phòng 40 người 600.000đ, Phòng 20 người 400.000đ, Văn phòng.
- Phòng Văn phòng thuê cố định **12.800.000đ/tháng chưa VAT**. "Chưa khai thác" nghĩa là chưa có lớp học thuê tại phòng đó.
- VAT: tính cho giáo viên là **10%**; nghiệm thu phòng (số trả cho trung tâm đào tạo) là **8%**.
- Chu kỳ nghiệm thu phòng: ngày 26 tháng trước → ngày 25 tháng này. Buổi sau ngày 25 và buổi chưa nghiệm thu chuyển sang tháng sau.
- Giáo viên dạy thay: lương buổi đó trả cho giáo viên dạy thay.
- Buổi bù: tính thêm tiền. Bù mà thuê phòng thì tăng tiền phòng; bù mà học online thì chỉ trả lương giáo viên.
- Giảm giá: có nhiều loại, chưa xác định hết; có học sinh đặc biệt được giảm 50% xuyên suốt năm học.

## 3. Thiết kế hệ thống

### 3.1 Nguyên tắc chung

- Một nguồn dữ liệu duy nhất: mọi con số tính ra từ lịch học, điểm danh và khoản thu.
- Mọi thông số đều nằm trong mục Cài đặt, chỉnh được, có hiệu lực theo thời gian.
- Mọi thay đổi về giá, điểm danh, khoản thu đều ghi nhật ký.

### 3.2 Lớp học → Học sinh → Hồ sơ học sinh

- Danh sách lớp hiển thị ngay: tên lớp, môn, khối, giáo viên, trợ giảng, phòng, thứ + giờ học, sĩ số, học phí/buổi tháng hiện tại, trạng thái.
- Vào một lớp: các thẻ Học sinh, Lịch học và buổi học, Điểm danh, Học phí, Nghiệm thu phòng.
- Danh sách học sinh trong lớp: tên, trường, SĐT, ngày bắt đầu, trạng thái (đang học / bảo lưu / đã nghỉ / chuyển lớp), buổi đã học trong tháng, học phí tháng, đã đóng, còn nợ.
- Hồ sơ học sinh: thông tin cá nhân (tên, trường, SĐT học sinh, họ tên phụ huynh, SĐT phụ huynh, ngày bắt đầu, ngày nghỉ); học phí (tổng cần đóng, đã đóng, còn nợ, đóng dư chuyển tháng sau; lịch sử đóng tiền gồm ngày, số tiền, tiền mặt/chuyển khoản, người thu, phân bổ vào tháng nào); buổi học (ngày, đi học / nghỉ có phép / nghỉ không phép / học online / nghỉ do trung tâm / học bù).

**Cách tính học phí tháng của một học sinh:**

- Buổi tính tiền = các buổi trong tháng nằm trong thời gian học của học sinh (từ ngày bắt đầu đến ngày nghỉ hoặc bảo lưu), trừ các buổi lớp nghỉ do trung tâm.
- Học phí tháng = buổi tính tiền × đơn giá/buổi của tháng đó (của lớp đó) − giảm giá (nếu có).
- Học sinh nghỉ có phép hay không phép: vẫn tính tiền, chỉ ghi nhận điểm danh.
- Học sinh học online trong buổi offline: tính tiền bình thường, điểm danh ghi "online".
- Cả lớp học online một buổi: tính tiền bình thường, không tính tiền phòng buổi đó.
- Vào giữa tháng: chỉ tính buổi từ ngày bắt đầu. Nghỉ hoặc bảo lưu giữa tháng: chỉ tính đến ngày nghỉ/bảo lưu.

**Chỗ nhập "nghỉ" (2 chỗ, hệ quả khác nhau, hệ thống tự tính lại ngay):**

- Điểm danh học sinh: nghỉ có phép/không phép, học online — chỉ ghi nhận, không làm giảm học phí.
- Buổi học của lớp: hủy buổi do trung tâm (giáo viên nghỉ đột xuất không có người dạy thay, phòng có vấn đề, nghỉ lễ) — làm giảm buổi tính tiền của cả lớp trong tháng.

**Đơn giá và giảm giá:**

- Đơn giá/buổi theo tháng, theo lớp, chỉnh được trong Cài đặt. Học sinh đã đóng trước giữ giá cũ cho phần đã đóng.
- Giảm giá là dòng riêng trong hóa đơn tháng: loại giảm (phần trăm, số tiền cố định, miễn phí một số buổi), phạm vi (học sinh, lớp, tháng), lý do, người duyệt, thời hạn. Hỗ trợ giảm 50% xuyên suốt năm học cho học sinh đặc biệt. Khi hoàn phí cho học sinh đang được giảm giá, số hoàn tính trên số tiền thực tế sau giảm.

**Phân bổ tiền đóng:**

- Khoản thu phân bổ vào tháng nợ cũ nhất trước; đóng dư tự thành số dư chuyển tháng sau.
- Đóng một lần cho nhiều tháng: hệ thống tự tách theo từng tháng.

**Các trường hợp phải tính và kiểm thử:** vào giữa tháng; vào giữa tháng đúng buổi lớp nghỉ do trung tâm; nghỉ giữa tháng và hoàn phí (cả 3 mức 100% / 50% / 0%); chuyển lớp (số dư chuyển sang, lớp đắt hơn đóng thêm phần chênh, rẻ hơn không hoàn); bảo lưu; nghỉ có phép nhiều buổi liền nhưng vẫn đóng đủ tiền tháng; cả lớp nghỉ đột xuất một buổi; học bù thay cho buổi đã hủy và học bù ngoài kế hoạch; lớp không có buổi nào trong tháng; học sinh học 2 lớp cùng lúc; đơn giá thay đổi giữa kỳ; giảm giá theo phần trăm + vào giữa tháng + hoàn phí cùng lúc; đóng thiếu một phần rồi đóng tiếp tháng sau; đóng tiền mặt và chuyển khoản cần đối soát.

### 3.3 Nhân sự

- Danh sách: tên, vai trò, SĐT, lớp phụ trách, trạng thái.
- Hồ sơ: thông tin cá nhân, vai trò, ngày bắt đầu làm việc, lương (giáo viên/trợ giảng theo buổi, nhân sự bộ phận theo tháng), BHXH, lớp đang dạy/hỗ trợ, lịch sử chấm công, lịch sử lương.
- Giáo viên lớp liên kết có thêm thẻ đối soát tháng: học phí đã thu, phí quản lý, tiền phòng, lương giáo viên, lương trợ giảng, cần đóng/hoàn lại, số dư chuyển tháng sau.
- Phân quyền: giáo viên chỉ xem lớp của mình và đối soát của mình; trợ giảng xem lớp mình hỗ trợ; nhân sự bộ phận nhập liệu; quản lý xem tài chính và duyệt.

### 3.4 Chấm công

- Một bảng chấm công tháng duy nhất cho giáo viên và trợ giảng. Hàng là từng người, cột là từng ngày trong tháng (ghi thứ, Chủ nhật tô màu), ô là trạng thái: đi dạy, nghỉ có phép, nghỉ không phép, dạy online, dạy bù, chưa xác nhận.
- Hệ thống tự điền trước buổi dự kiến từ thời khóa biểu; người chấm chỉ xác nhận hoặc sửa.
- Cuối bảng tự tổng hợp: số buổi đã dạy trong tháng theo loại phòng (đối chiếu nghiệm thu phòng), lương tạm tính.
- Nghỉ đột xuất: nhập lý do, chọn hủy buổi hoặc xếp giáo viên dạy thay. Hủy buổi thì học phí tháng của cả lớp giảm một buổi, tiền phòng buổi đó bằng 0, giáo viên không tính lương buổi đó. Dạy thay thì ghi rõ người dạy thay, lương tính cho người dạy thay, học phí và tiền phòng không đổi.
- Các trường hợp khác: giáo viên dạy 2 lớp một ngày ở 2 phòng khác nhau; trợ giảng hỗ trợ nhiều lớp; nghỉ có kế hoạch trước thì xếp người dạy thay từ trước; chấm công sai rồi sửa lại sau (cần quyền quản lý, ghi nhật ký, tính lại tự động).

### 3.5 Nghiệm thu phòng

- Danh sách phòng với đơn giá theo buổi, cài đặt được, cộng VAT (10% phía giáo viên, 8% phía nghiệm thu trả cho trung tâm đào tạo).
- Thời khóa biểu sinh nhật ký phòng theo tuần tự động.
- Hằng ngày xác nhận thực tế từng buổi: dạy, nghỉ đột xuất, đổi phòng, học online, thêm buổi.
- Ngày 25 khóa chu kỳ, hệ thống tự tính B1 (buổi theo giáo viên và loại phòng), B2 (buổi theo lớp và loại phòng), B3 (tổng phòng đến ngày 25 theo tuần và loại phòng), B4 (tiền phòng: còn lại tháng trước + phát sinh trong tháng, VAT). Quản lý duyệt nghiệm thu thì tiền phòng thành khoản phải thu.
- Buổi sau ngày 25 và buổi chưa xác nhận tự chuyển sang chu kỳ sau.
- Các trường hợp: nghỉ đột xuất (hủy thì không tính tiền phòng, dạy thay thì tính bình thường); thêm lớp/buổi trong tuần (kiểm tra trùng phòng và trùng giờ trước khi lưu, tiền phòng tính từ buổi đó); đổi phòng giữa kỳ (tính lại tiền phòng từ ngày đổi, giữ lịch sử phòng đã dùng theo buổi); dạy online (không tính tiền phòng); nghỉ lễ (nhập một lần vào lịch nghỉ chung); phòng dùng ngoài dạy học (nhập tay buổi sử dụng); hai lớp trùng phòng cùng giờ (cảnh báo và chặn); tiền phòng tháng trước còn lại chuyển sang thành số dư đầu kỳ; phòng Văn phòng thuê cố định 12.800.000đ/tháng, phần chưa có lớp thuê là "chưa khai thác".

### 3.6 Cài đặt tính toán

- Tạo lớp: nhập ngày bắt đầu, thứ học, giờ học, phòng, giáo viên, trợ giảng, học phí/buổi → hệ thống tự sinh lịch tất cả buổi học của lớp. Sau đó chỉ nhập ngày nghỉ là hệ thống tự tính lại số buổi và học phí của tháng.
- Lịch nghỉ chung toàn trung tâm (Tết, lễ) nhập một lần, áp cho mọi lớp.
- Mục Cài đặt gồm: học phí/buổi theo lớp và tháng; tỷ lệ phí quản lý theo giáo viên; đơn giá phòng theo loại và mức VAT; lương giáo viên/trợ giảng theo buổi; chính sách hoàn phí và bảo lưu; chu kỳ chốt (nghiệm thu phòng ngày 25, chốt học phí cuối tháng, ngày trả lương); các loại giảm giá và quy tắc áp dụng; danh sách ngày nghỉ chung. Tất cả có hiệu lực theo thời gian.
- Mỗi buổi học có chế độ offline / online / kết hợp, kèm ô ghi chú. Lớp chuyển online cả buổi: ghi chú lý do, không tính tiền phòng. Học sinh học online trong buổi offline: điểm danh ghi "online" kèm ghi chú. Giáo viên dạy online ghi nhận tương tự.

### 3.7 Đối soát và báo cáo

- Đối soát giáo viên liên kết theo tháng; dòng tiền, lợi nhuận gộp và lợi nhuận thuần theo tháng; công nợ học sinh; tiền phòng phải thu; báo cáo theo tháng, theo giáo viên, theo lớp; xuất Excel.

## 4. Phong cách giao diện

- Tối giản, gọn gàng. Bảng màu HEX: xanh dương, đỏ, vàng.

## 5. Số liệu tham khảo (tháng 11/2026, từ bảng thống kê)

- Doanh thu lớp tự mở 48.825.000đ; học phí lớp liên kết 329.099.999đ; giáo viên cần đóng 178.542.500đ.
- Lợi nhuận gộp 50.937.500đ; chi phí chung 28.354.000đ; lợi nhuận thuần 22.583.500đ.

## 6. Việc còn lại

- Nhập dữ liệu học sinh và công nợ đầu kỳ từ 2 Google Sheets vào database hệ thống.
- Xác định đầy đủ các loại giảm giá đang áp dụng.
- Bàn giao bản chạy thử để bấm thử luồng thu học phí, phân bổ và nghiệm thu phòng, rồi xây đầy đủ.
