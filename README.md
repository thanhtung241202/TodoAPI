Tài liệu API Todo: mô tả cách triển khai và kết quả kiểm tra cho một API Todo đơn giản sử dụng ASP.NET Core Minimal APIs.

Các tính năng
1. CRUD Operations:
+ GET: Lấy danh sách tất cả các công việc, các công việc đã hoàn thành, hoặc một công việc cụ thể dựa theo ID.
+ POST: Tạo một công việc mới.
+ PUT: Cập nhật thông tin công việc dựa theo ID.
+ DELETE: Xóa một công việc dựa theo ID.
2.Nhóm routing với MapGroup:
+ Các endpoint được tổ chức theo một URL tiền tố chung (/todoitems), giúp giảm sự lặp lại và cải thiện khả năng bảo trì.
3. TypedResults cho phản hồi:
+ Tăng khả năng kiểm thử và tự động sinh tài liệu OpenAPI bằng cách sử dụng các phản hồi kiểu mạnh như Ok<T>, Created, và NoContent.
4. Triển khai DTO:
+ Sử dụng lớp TodoItemDTO để tránh over-posting, ẩn các trường nhạy cảm (ví dụ: Secret), và tối ưu hóa payload.
+ Đảm bảo chỉ cung cấp các dữ liệu cần thiết cho người dùng API.
5. Cơ sở dữ liệu trong bộ nhớ (In-Memory Database):
+ Được sử dụng cho mục đích minh họa, cần khởi tạo lại mỗi khi ứng dụng khởi động.

Kết quả kiểm tra
1.Endpoint PUT:
+ Cập nhật thành công công việc có ID 1, thay đổi tên thành "feed fish" và trạng thái isComplete thành false.
+ Trả về phản hồi 204 No Content khi cập nhật thành công.
2. Endpoint DELETE:
+ Xóa thành công công việc có ID 1.
+ Trả về phản hồi 204 No Content khi xóa thành công.
3. Xác thực DTO:
+ Kiểm tra các phản hồi từ POST và GET, xác nhận trường Secret đã được ẩn khỏi payload.
4. Tổ chức nhóm:
+ Kiểm tra các endpoint nhóm (/todoitems), xác nhận tính năng hoạt động tương tự như khi không nhóm.
5. Xác minh TypedResults:
+ Đảm bảo kiểu phản hồi chính xác (ví dụ: Ok<Todo[]>, NotFound) trong quá trình kiểm thử.

Lợi ích chính
+ Đơn giản hóa bảo trì mã nguồn: Routing theo nhóm và tổ chức theo phương thức giúp giảm sự lặp lại và tăng khả năng đọc mã.
+ Nâng cao bảo mật: Sử dụng DTO giúp tránh over-posting và ẩn dữ liệu nhạy cảm.
+ Cải thiện kiểm thử: TypedResults cho phép kiểm tra chính xác kiểu phản hồi.
+ Dễ sử dụng: Cơ sở dữ liệu trong bộ nhớ hỗ trợ kiểm thử nhanh và tạo mẫu hiệu quả.
