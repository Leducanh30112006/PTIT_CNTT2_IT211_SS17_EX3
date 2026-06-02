## So sánh giữa `@Secured` và `@PreAuthorize`

Với yêu cầu **"Chỉ người tạo ra một tác vụ hoặc PO mới được phép xóa tác vụ đó"**, annotation `@PreAuthorize` là lựa chọn tối ưu và bắt buộc thay vì `@Secured`.

### Bảng so sánh chi tiết

| Đặc điểm | `@Secured` | `@PreAuthorize` |
| :--- | :--- | :--- |
| **Nguồn gốc** | Thuộc về Spring Security từ các phiên bản rất cũ. | Ra đời từ Spring Security 3.0 (hiện đại hơn). |
| **Khả năng xử lý** | Chỉ kiểm tra được danh sách các Role tĩnh (ví dụ: `@Secured({"ROLE_PO", "ROLE_SM"})`). | Hỗ trợ ngôn ngữ biểu diễn **SpEL** *(Spring Expression Language)* cực kỳ mạnh mẽ. |
| **Độ linh hoạt** | Không thể đọc tham số truyền vào phương thức, không gọi được các Bean Spring khác để check logic. | Có thể truy cập các tham số của hàm (như `taskId`), lấy thông tin user hiện tại (`authentication.name`), và gọi các hàm nghiệp vụ từ Service. |