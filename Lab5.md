**#NguyenDinhLuu_4451050894
#Lab5
#Dựa trên mô tả chi tiết về các ca sử dụng và thiết kế từng thành phần ở bài Lab4, hệ thống Payroll System có thể được chia thành các hệ thống con (subsystems) chính như sau:**
**1. Authentication Subsystem (Hệ thống xác thực):**
- Mô tả: Đảm nhiệm việc quản lý đăng nhập và xác thực người dùng.
- Thành phần chính:
    + LoginForm (boundary): Giao diện nhập tên đăng nhập và mật khẩu.
    + AuthenticationSystem (control): Xử lý nghiệp vụ xác thực.
    + UserDatabase (entity): Cơ sở dữ liệu người dùng.
- Chức năng chính:
    + Kiểm tra thông tin đăng nhập
    + Quản lý phiên làm việc (sessions)
**2. Timecard Management Subsystem (Quản lý bảng chấm công):**
- Mô tả: Quản lý các thông tin chấm công của nhân viên.
- Thành phần chính:
    + TimecardForm (boundary): Giao diện nhập và xem thông tin chấm công.
    + TimecardController (control): Xử lý logic liên quan đến bảng chấm công.
    + Timecard (entity): Dữ liệu bảng chấm công.
    + ProjectManagementDatabase (subsystem): Quản lý mã dự án.
- Chức năng chính:
    + Lấy và lưu bảng chấm công.
    + Tương tác với ProjectManagementDatabase để lấy mã dự án.
**3.  Payroll Processing Subsystem (Xử lý bảng lương):**
- Mô tả: Tự động hóa việc tính toán và xử lý lương.
- Thành phần chính: 
    + PayrollController (control): Xử lý logic nghiệp vụ liên quan đến lương.
    + Employee, Paycheck, Timecard (entities): Dữ liệu liên quan đến nhân viên và bảng lương.
    + SystemClockInterface (boundary): Xác định thời điểm trả lương.
    + BankSystem (subsystem): Xử lý giao dịch ngân hàng.
    + PrintService (subsystem): Xử lý việc in phiếu lương.
- Chức năng chính:
    + Tính lương theo loại nhân viên (giờ, cố định, hoa hồng).
    + Xử lý giao dịch chuyển lương.
    + In phiếu lương.
**4. Bank Interaction Subsystem (Tương tác ngân hàng):**
- Mô tả: Tích hợp với các hệ thống ngân hàng để thực hiện giao dịch.
- Thành phần chính:
    + IBankSystem (interface): Định nghĩa giao diện giao tiếp ngân hàng.
    + BankSystem (subsystem): Hiện thực giao tiếp với ngân hàng.
    + BankInformation, Paycheck (entities): Dữ liệu cần thiết cho giao dịch.
- Chức năng chính:
    + Thực hiện chuyển khoản lương.
    + Kiểm tra trạng thái giao dịch.
**5. Printing Subsystem (In phiếu lương):**
- Mô tả: Quản lý in ấn cho phiếu lương nhân viên 
- Thành phần chính:
    + IPrintService (interface): Giao diện chuẩn hóa cho dịch vụ in.
    + PrintService (subsystem): Hiện thực logic in phiếu lương.
    + Paycheck (entity): Dữ liệu phiếu lương.
- Chức năng chính:
    + In hoặc xuất phiếu lương dưới dạng tệp.
    + Quản lý trạng thái và kết quả in.
**6. Project Management Subsystem (Quản lý dự án):**
- Mô tả: Cung cấp mã dự án cho các hoạt động chấm công.
- Thành phần chính:
    + IProjectManagementDatabase (interface): Giao diện với hệ thống quản lý dự án.
    + ProjectManagementDatabase (subsystem): Hiện thực việc lấy dữ liệu dự án.
- Chức năng chính:
    + Lấy danh sách mã dự án từ cơ sở dự liệu.
    + Tích hợp với hệ thống quản lý dự án kế thừa.
**7. System Clock Subsystem (Đồng bộ thời gian hệ thống):**
- Mô tả: Quản lý và chuẩn hóa việc sử dụng thời gian trong hệ thống.
- Thành phần chính:
    + SystemClockInterface (boundary): Lấy thời gian từ hệ thống.
- Chức năng chính:
    + Đồng bộ thời gian trong các tác vụ (trả lương, nộp bảng chấm công).
    + Giảm sai lệnh thời gian giữa các thành phần.
**8. Distribution Subsystem (Hệ thống phân phối):**
- Mô tả: Cho phép các thành phần của hệ thống Payroll System giao tiếp và hoạt động trên môi trường phân tán.
- Thành phần chính:
      + IPayrollController: Giao diện điều khiển từ xa cho Payroll.
      + Naming Service: Hỗ trợ tra cứu các đối tượng từ xa.
- Chức năng chính: Hỗ trợ truy cập từ xa qua mạng.
- Dữ liệu: Kết nối và xử lý dữ liệu phân tán.
**Về kiến trúc tổng thể:**
- Hệ thống được tổ chức theo mô hình phân tầng:
    + Application Layer (Tầng ứng dụng): Bao gồm các giao diện như LoginForm, TimecardForm.
    + Business Services Layer (Tầng dịch vụ nghiệp vụ): Xử lý logic nghiệp vụ qua các controller như PayrollController, TimecardController.
    + Middleware Layer (Tầng trung gian): Các interface và subsystem như IBankSystem, IPrintService.
    + Data Layer (Tầng dữ liệu): Các entity như Timecard, Paycheck, Employee.
**Lý do tổ chức theo hệ thống con:**
    + Modularity: Tách biệt chức năng rõ ràng giúp bảo trì dễ dàng hơn.
    + Encapsulation: Các interface (như IBankSystem, IPrintService) che giấu sự phức tạp của hệ thống bên ngoài.
    + Scalability: Hỗ trợ mở rộng dễ dàng nhờ kiến trúc module hóa.
    + Flexibility: Dễ tích hợp với các hệ thống kế thừa hoặc bên thứ ba.


