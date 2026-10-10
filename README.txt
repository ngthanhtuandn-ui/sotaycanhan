SỔ TAY CÁ NHÂN & LỊCH CA TRỰC — BẢN PWA THỬ NGHIỆM

CÁC FILE
- index.html: ứng dụng chính, giữ các tab Lịch Ca Tuần / Báo Cáo Ca / Việc Phát Sinh.
- manifest.webmanifest: cấu hình cài đặt PWA.
- sw.js: cache app shell để mở lại offline sau lần tải online đầu tiên.
- icons/: biểu tượng ứng dụng.

CÁCH THỬ NHANH TRÊN MÁY TÍNH
1. Mở index.html bằng Chrome/Edge. Các chức năng dữ liệu cơ bản hoạt động, nhưng PWA/Service Worker và thông báo có thể không hoạt động khi mở file://.
2. Thử lưu báo cáo, việc phát sinh, đính kèm ảnh; bấm Sao Lưu để tải JSON.
3. Thử Phục Hồi với file JSON đã xuất.

CÀI PWA TRÊN XIAOMI HYPEROS
1. Đưa toàn bộ thư mục lên hosting HTTPS (ví dụ Netlify; không chỉ tải riêng index.html).
2. Mở URL HTTPS bằng Chrome trên điện thoại, tải trang một lần khi có mạng.
3. Menu Chrome (⋮) → Cài đặt ứng dụng / Thêm vào màn hình chính.
4. Mở app, bấm “🔔 Bật Thông Báo” và cho phép. Bấm “🔊 Thử Chuông” để cấp quyền phát âm thanh sau tương tác.
5. Trên HyperOS, nếu có: Cài đặt → Ứng dụng → Quản lý ứng dụng → Chrome hoặc app PWA → Pin/tiết kiệm pin → Không hạn chế; bật Tự khởi động nếu mục này xuất hiện. Tên menu tùy phiên bản.
6. Vào chế độ máy bay để kiểm tra app vẫn mở offline.

GIỚI HẠN BÁO THỨC QUAN TRỌNG
PWA chỉ kiểm tra giờ và phát chuông khi trang đang chạy; Notification API là best-effort. Service Worker không được phép chạy vòng lặp liên tục và không thể đảm bảo đánh thức app đúng giờ khi Chrome/tiến trình bị HyperOS dừng, máy khởi động lại hoặc tiết kiệm pin. Với giờ trực quan trọng, hãy tạo thêm báo thức trong ứng dụng Đồng hồ của Xiaomi.

BẢO TOÀN DỮ LIỆU
- Giữ nguyên các khóa localStorage hiện có: camp_reports_v2, camp_issues_v2, camp_weekly_shifts.
- Không tự động xóa hoặc chuyển đổi dữ liệu cũ.
- Khi phục hồi JSON, app lưu bản dữ liệu ngay trước khi phục hồi trong localStorage với khóa camp_pre_restore_backup_v1.
- Dữ liệu localStorage gắn với nguồn gốc website (domain + protocol). Nếu chuyển sang domain/hosting khác, hãy xuất JSON ở bản cũ rồi nhập vào bản mới.
- Ảnh được lưu trong JSON/localStorage và có thể làm đầy dung lượng trình duyệt; nên sao lưu định kỳ.

GHI CHÚ
Bản này sửa cách chống báo trùng và lưu dấu đã báo, thêm thông báo trình duyệt và thống kê nhanh. Không có đồng bộ nhiều thiết bị/cloud. Hãy kiểm tra các chức năng trên bản thử trước khi dùng cho dữ liệu quan trọng.
