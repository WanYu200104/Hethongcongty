# Hệ thống quản lý trung tâm đào tạo — Công ty TNHH Đào tạo Đắc Thành

Hệ thống website quản lý trung tâm đào tạo, thay thế quản lý bằng Google Sheets.

## Vấn đề hiện tại

- Khó quản lý học phí học sinh đóng vào.
- Dễ bỏ sót việc phân bổ tiền học cho học sinh (học sinh đóng một lúc nhiều buổi nhưng mỗi tháng chỉ học 4–5 buổi, số dư phải phân bổ sang các tháng sau).

## Hệ thống gồm

1. **Lớp học → Học sinh → Hồ sơ học sinh**: danh sách lớp (thấy ngay giáo viên, trợ giảng), danh sách học sinh trong lớp, hồ sơ học sinh (thông tin cá nhân, tổng cần đóng, lịch sử đóng tiền, tình trạng học phí). Học phí tháng tự tính từ buổi học.
2. **Nhân sự**: danh sách nhân sự, bấm vào xem hồ sơ cá nhân; đối soát tháng cho giáo viên lớp liên kết.
3. **Chấm công**: một bảng chấm công tháng duy nhất cho giáo viên và trợ giảng.
4. **Nghiệm thu phòng**: nhật ký phòng theo tuần, tổng hợp B1/B2/B3/B4, chu kỳ 26 tháng trước → 25 tháng này.
5. **Cài đặt tính toán**: mọi tỷ lệ, đơn giá, lịch học, chính sách đều chỉnh được — không hard-code.

## Nguyên tắc

- Một nguồn dữ liệu duy nhất: mọi con số đều tính ra từ lịch học, điểm danh và khoản thu.
- Mọi thông số đều có trong mục Cài đặt và có hiệu lực theo thời gian.
- Mọi thay đổi về giá, điểm danh, khoản thu đều ghi nhật ký (ai sửa, lúc nào).

## Tài liệu

- `docs/thiet-ke-he-thong.md` — thiết kế hệ thống chi tiết (đã chốt với người dùng ngày 2026-11-13).

## Dữ liệu gốc

Dữ liệu vận hành hiện tại nằm trên 2 Google Sheets của trung tâm (18 lớp, khoảng 320 học sinh, khối 6–12, Toán/Văn/Anh văn). Dữ liệu này được dùng làm database cho hệ thống (xem thiết kế chi tiết).

## Trạng thái

- Bản chạy thử (prototype) đang được xây dựng trong Muse; sẽ bàn giao để bấm thử trước khi xây đầy đủ.
- Phong cách: tối giản, gọn gàng; bảng màu HEX: xanh dương, đỏ, vàng.
