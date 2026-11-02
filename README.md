# (Bài tập tổng hợp) Ngày Đầu Thực Tập Dev Tại Công Ty Công Nghệ

## Phần A – Profile & Bookmark

1. Xung đột phiên:
   - Dùng chung 1 Profile khiến Cookies và Session Storage của tài khoản cá nhân và công ty bị ghi đè lẫn nhau, dẫn đến hiện tượng văng phiên đăng xuất liên tục.

2. Mô hình 3 Profile chuẩn Developer:

| Tên Profile | Mục đích sử dụng |
| :--- | :--- |
| `Personal` | Dùng cho tài khoản cá nhân, mạng xã hội và GitHub cá nhân. |
| `Company_Work` | Dùng riêng cho công việc chính và GitHub công ty. |
| `Sandbox/Test` | Dùng để thử nghiệm tính năng web và kiểm thử mã nguồn. |

3. Cấu trúc thư mục Bookmark:
   * 01_Work_Internal 
   * 02_Dev_Tools 
   * 03_Learning_Reference 

4. Cho đồng nghiệp mượn máy 5 phút:
   - Cho dùng Guest Profile hoặc cửa sổ Incognito để đảm bảo không lộ dữ liệu cá nhân, tự động xóa sạch lịch sử và cookies khi tắt.

## Phần B – Chọn Đúng Extension Hỗ Trợ

1. Lựa chọn Extension: 
   - Chọn nhóm Dev Suite. Hai nhóm Productivity Suite và Security Suite không có tính năng định dạng dữ liệu API thô.
2. Cấu hình quyền Site Access:
   - Chọn On click. Giúp giới hạn quyền, chỉ chạy tiện ích khi người dùng chủ động nhấp vào biểu tượng, tránh quét ngầm dữ liệu trang nội bộ.

## Phần C – Phân Tích Luồng HTTP Request

1. 4 giai đoạn xử lý:
   - DNS Lookup -> TCP Handshake -> HTTP Request / Response -> Rendering.
2. So sánh mã trạng thái (Status Code):

| Mã trạng thái | Ý nghĩa | Lỗi nằm ở đâu? | Hướng debug ban đầu |
| :--- | :--- | :--- | :--- |
| 404 Not Found | Không tìm thấy tài nguyên. | Phía Client. | Kiểm tra chính tả đường dẫn URL. |
| 500 Internal Error | Lỗi máy chủ nội bộ. | Phía Server. | Kiểm tra Server log. |

3. Tab DevTools xem Status:
   - Mở Network Tab vì đây là tab ghi lại toàn bộ request/response theo thời gian thực.

## Phần D – Chẩn Đoạn Cache và Cookies

1. Lỗi sửa CSS nhưng F5 vẫn hiển thị bản cũ:
   - Nguyên nhân do Browser Cache. Khắc phục bằng cách thực hiện Hard Reload .
2. Rủi ro khi Cookie `session_id` thiếu `HttpOnly`:
   - Mã độc JavaScript có thể đọc được giá trị cookie qua `document.cookie`. Tên loại tấn công là XSS.
3. **Đăng xuất nhưng giữ nguyên Cache ảnh/CSS:**
   - Xóa thủ công đúng cookie `session_id` trong tab **Application**, không xóa toàn bộ Browser Data.

## Phần E – Debug Bằng Inspect Element và Network Tab

1. **Sửa màu nút "Đăng nhập" trực tiếp trên trình duyệt:**
   - Nhấn `Ctrl + Shift + C` chọn nút -> Tại bảng **Styles** trong tab **Elements**, sửa thuộc tính `background-color` để xem trước kết quả.
2. Quy trình 4 Bước Debug API lỗi:
   - Bước 1: Reproduce & Identify.
   - Bước 2: Inspect Details.
   - Bước 3: Isolate.
   - Bước 4: Fix & Verify.
3. **2 thao tác trên Network Tab để lọc API và bỏ qua Cache:**
   - Chọn bộ lọc **Fetch/XHR**.
   - Tích chọn ô **Disable cache**.
