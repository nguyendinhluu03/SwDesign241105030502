#NguyenDinhLuu-4451050894
#Lab4
**Dựa vào kết quả phân tích ca sử dụng (use case analysis) và các phần tử thiết kế (design elements) trong file đính kèm, dưới đây là thiết kế các ca sử dụng cho hệ thống "Payroll System":**
**1. Login:**
**- Mô tả:** Ca sử dụng này cho phép người dùng hệ thống đăng nhập bằng cách nhập tên đăng nhập và mật khẩu.
**- Thiết kế:**
  + Thành phần tham gia:
      **LoginForm (boundary):** giao diện nhập tên đăng nhập và mật khẩu.
      **User (actor):** người dùng của hệ thống.
      **AuthenticationSystem (control):** kiểm tra thông tin xác thực.
  + Luồng chính:
      B1: Người dùng nhập tên đăng nhập và mật khẩu vào **LoginForm.**
      B2: **LoginForm** gửi thông tin đến **AuthenticationSystem** để xác thực.
      B3: **AuthenticationSystem** xác thực thông tin với cơ sở dữ liệu.
      B4: Nếu thông tin hợp lệ, cho phép truy cập vào hệ thống.
**- Lý do thiết kế:**
  + Tuân thủ mô hình boundary-control-entity để đảm bảo tính độc lập giữa giao diện, xử lý nghiệp vụ và dữ liệu.
  + Giao diện **LoginForm** nằm trong gói **Security:GUI Framework** để đảm bảo tích hợp chặt chẽ với hệ thống bảo mật.
**2. Maintain Timecard:**
**- Mô tả:** Ca sử dụng này cho phép nhân viên quản lý bảng chấm công của mình, bao gồm xem, nhập và lưu dữ liệu chấm công.
**- Thiết kế:**
  + Thành phần tham gia:
      **TimecardForm (boundary):** giao diện để hiển thị và nhập bảng chấm công.
      **Employee (actor):** nhân viên sử dụng hệ thống.
      **TimecardController (control):** xử lý các tác vụ liên quan đến bảng chấm công.
      **ProjectManagementDatabase (entity):** cung cấp thông tin mã dự án.
      **Timecard (entity):** lưu trữ thông tin bảng chấm công.
  + Luồng chính:
      B1: Nhân viên mở **TimecardForm.**
      B2: **TimecardForm** yêu cầu **TimecardController** lấy bảng chấm công hiện tại và mã dự án từ **ProjectManagementDatabase.**
      B3: Nhân viên nhập số giờ làm việc.
      B4: **TimecardController** cập nhật và lưu dữ liệu vào **Timecard.**
**- Lý do thiết kế:**
  + Phân tầng kiến trúc rõ ràng giữa giao diện người dùng, logic xử lý nghiệp vụ, và lớp lưu trữ dữ liệu.
  + Sử dụng **interface IProjectManagementDatabase** để tương tác với hệ thống quản lý dự án cũ.
**3. Run Payroll:**
**- Mô tả:** Tự động tính toán lương và phát lương cho nhân viên.
**- Thiết kế:**
  + Thành phần tham gia:
      **PayrollController (control):** điều khiển quá trình chạy lương.
      **SystemClockInterface (boundary):** kiểm tra ngày trả lương.
      **BankSystem và IBankSystem (boundary):** thực hiện giao dịch ngân hàng.
      **PrintService và IPrintService (boundary):** in phiếu lương.
      **Timecard, Employee, Paycheck, PurchaseOrder (entity):** lưu trữ dữ liệu cần thiết.
  + Luồng chính:
      B1: **PayrollController** kiểm tra thời gian từ **SystemClockInterface.**
      B2: Với mỗi nhân viên, hệ thống:
          Tính toán lương dựa trên **Timecard** và loại nhân viên **(HourlyEmployee, SalariedEmployee, CommissionedEmployee)**.
          Tạo phiếu lương **(Paycheck).**
          Thực hiện in hoặc gửi phiếu lương qua **BankSystem.**
      B3: Lưu dữ liệu phát lương vào cơ sở dữ liệu.
**- Lý do thiết kế:**
  + Sử dụng các **interface** như **IBankSystem** và **IPrintService** để đảm bảo tính linh hoạt và khả năng mở rộng.
  + Phân tầng kiến trúc đảm bảo tách biệt logic xử lý nghiệp vụ với các hệ thống bên ngoài.
**4. Giao dịch với hệ thống ngân hàng (BankSystem Subsystem):**
**- Mô tả:** Hệ thống tương tác với các ngân hàng bên ngoài để thực hiện các giao dịch, như chuyển khoản lương qua tài khoản.
**- Thiết kế:**
  + Thành phần tham gia:
      **PayrollController** (control): điều khiển quá trình thực hiện giao dịch.
      **IBankSystem** (interface): đại diện giao tiếp với hệ thống ngân hàng.
      **BankSystem** (subsystem): hiện thực giao tiếp với hệ thống ngân hàng bên ngoài.
      **Paycheck, BankInformation** (entity): thông tin cần thiết cho giao dịch.
  + Luồng chính: 
      B1: **PayrollController** gọi **IBankSystem** với thông tin phiếu lương **(Paycheck)** và thông tin ngân hàng **(BankInformation)**.
      B2: **IBankSystem** chuyển yêu cầu đến **BankSystem.**
      B3: **BankSystem** thực hiện giao dịch với ngân hàng.
      B4: Hệ thống trả kết quả về cho **PayrollController.**
**- Lý do thiết kế:**
  + Encapsulation: Interface **IBankSystem** đóng vai trò trung gian, giúp giảm phụ thuộc vào các thay đổi trong hệ thống ngân hàng.
  + Mô hình client-subsystem: Tương tác giữa **PayrollController** và **BankSystem** qua interface chuẩn hóa.
**5. In phiếu lương (PrintService Subsystem):**
**- Mô tả:** Hệ thống tạo và in các phiếu lương để cung cấp cho nhân viên.
**- Thiết kế:**
  + Thành phần tham gia:
      **PayrollController** (control): điều phối quá trình in phiếu lương.
      **IPrintService** (interface): giao diện với dịch vụ in.
      **PrintService** (subsystem): hiện thực giao tiếp với máy in.
      **Paycheck** (entity): thông tin phiếu lương cần in.
  + Luồng chính:
      B1: **PayrollController** gửi thông tin phiếu lương **(Paycheck)** và chỉ định máy in qua **IPrintService.**
      B2: **IPrintService** gọi **PrintService** để in phiếu lương.
      B3: **PrintService** thực hiện in và trả thông báo trạng thái.
**- Lý do thiết kế:**
  + Interface **IPrintService** giúp đảm bảo khả năng mở rộng, cho phép tích hợp với nhiều loại máy in khác nhau.
  + Subsystem **PrintService** tách biệt logic in ấn khỏi phần điều phối chính **(PayrollController).**
**6. Quản lý mã dự án (ProjectManagementDatabase Subsystem):**
**- Mô tả:** Cung cấp thông tin mã dự án (charge numbers) từ cơ sở dữ liệu quản lý dự án.
**- Thiết kế:**
  + Thành phần tham gia:
      **TimecardController** (control): điều phối việc lấy mã dự án.
      **IProjectManagementDatabase** (interface): giao diện với hệ thống quản lý dự án.
      **ProjectManagementDatabase** (subsystem): hiện thực giao tiếp với cơ sở dữ liệu.
  + Luồng chính:
      B1: **TimecardController** gửi yêu cầu đến **IProjectManagementDatabase** với tiêu chí lọc.
      B2: **IProjectManagementDatabase** chuyển yêu cầu đến **ProjectManagementDatabase.**
      B3: **ProjectManagementDatabase** truy xuất dữ liệu và trả danh sách mã dự án.
**- Lý do thiết kế:**
  + Encapsulation: Interface **IProjectManagementDatabase** cung cấp một điểm truy cập duy nhất, giảm sự phụ thuộc vào cấu trúc cơ sở dữ liệu.
  + Hỗ trợ khả năng tích hợp: Subsystem **ProjectManagementDatabase** cho phép tích hợp liền mạch với các hệ thống kế thừa.
**7. Đồng bộ thời gian hệ thống (System Clock Integration):**
**- Mô tả:** Sử dụng thời gian hệ thống để xác định các tác vụ, như ngày trả lương hoặc hạn chót nộp bảng chấm công.
**- Thiết kế:**
  + Thành phần tham gia:
      **SystemClockInterface** (boundary): giao diện đồng bộ thời gian.
      **PayrollController, TimecardController** (control): các thành phần sử dụng thời gian hệ thống.
  + Luồng chính:
      B1: Bộ điều khiển **(PayrollController hoặc TimecardController)** gọi SystemClockInterface để lấy thời gian hiện tại.
      B2: **SystemClockInterface** trả về thời gian hệ thống.
      B3: Bộ điều khiển thực hiện logic dựa trên thời gian (ví dụ: xác định ngày trả lương, kiểm tra hạn nộp bảng chấm công).
**- Lý do thiết kế:**
  + Subsystem clock giúp chuẩn hóa việc truy xuất thời gian trong toàn hệ thống.
  + Giảm rủi ro sai lệch thời gian khi nhiều thành phần truy cập thời gian trực tiếp.
**- Tổng kết, lý do thiết kế tổng quan:**
    - Thiết kế được xây dựng dựa trên mô hình OOAD (Object-Oriented Analysis and Design), đảm bảo khả năng tái sử dụng và dễ bảo trì.
    - Các thành phần giao tiếp với hệ thống bên ngoài (ngân hàng, máy in) được encapsulate qua các subsystem proxy và interface để giảm phụ thuộc.
    - Cấu trúc theo lớp (Application, Business Services, Middleware) giúp hệ thống dễ dàng mở rộng và tích hợp thêm tính năng.
    - Tính module hóa cao:
        + Các interface như **IBankSystem**, **IPrintService**, và **IProjectManagementDatabase** đảm bảo tính linh hoạt, giúp hệ thống dễ dàng thay đổi hoặc tích hợp với             các hệ thống bên ngoài.
    - Kiến trúc phân tầng:
        + Hệ thống được chia thành các tầng (Application, Business Services, Middleware) như đã chỉ định trong tài liệu, giúp dễ dàng bảo trì và mở rộng.
    - Phù hợp với nguyên tắc SOLID:
        + Subsystem và interface tuân theo nguyên tắc **Interface Segregation** và **Dependency Inversion**, tách biệt rõ ràng giữa logic nghiệp vụ và các hệ thống bên                ngoài.
