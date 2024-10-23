**#Lab1**
**Câu 1:** Phân tích kiến trúc
  - Các thành phần trong kiến trúc: 4 tầng
    + Presentation Layer (Tầng Giao Diện)
    + Application Layer (Tầng Ứng Dụng)
    + Integration Layer (Tầng Tích Hợp)
    + Data Layer (Tầng Dữ Liệu)
  - Giải thích lý do lựa chọn:
    + Tầng giao diện: Windows-based desktop interface được yêu cầu trong đề bài, cung cấp môi trường dễ sử dụng và phù hợp với các nhân viên trên nhiều địa        điểm khác       nhau.
    + Tầng ứng dụng: Tầng ứng dụng tách biệt giúp tăng tính module hóa của hệ thống, cho phép dễ bảo trì và mở rộng trong tương lai.
    + Tầng tích hợp: Vì hệ thống phải tích hợp với các hệ thống legacy (DB2) và ngân hàng, cần một tầng tích hợp để quản lý kết nối với các hệ thống này.
    + Tầng dữ liệu: Phân chia rõ ràng các chức năng xử lý dữ liệu giúp bảo mật và hiệu quả trong việc quản lý thông tin.
  - Ý nghĩa:
     + Presentation Layer:
         Kết nối giữa người dùng và hệ thống, cung cấp giao diện thân thiện.
     + Application Layer:
         Tầng này xử lý các logic nghiệp vụ liên quan đến việc quản lý thông tin chấm công, tính toán lương và hoa hồng, quản lý phương thức thanh toán, và tương tác với cơ          sở dữ liệu nhân viên và các hệ thống liên quan.
         Chịu trách nhiệm xử lý quy tắc trả lương theo từng loại nhân viên (giờ công, lương cứng, có hoa hồng), xử lý tăng ca và quản lý việc tạo các báo cáo liên quan cho           nhân viên.
     + Integration Layer: Quản lý giao tiếp giữa lớp nghiệp vụ và lớp truy cập dữ liệu
         Tầng này quản lý kết nối và tích hợp với các hệ thống bên ngoài như hệ thống cơ sở dữ liệu DB2 trên IBM mainframe và các hệ thống ngân hàng để xử lý giao dịch               chuyển khoản.
     + Data Layer: Gíup truy cập và quản lý cơ sở dữ liệu, thực hiện lưu trữ và truy xuất thông tin.
         Tầng này chứa cơ sở dữ liệu để lưu trữ thông tin nhân viên, bảng chấm công, phương thức thanh toán và các bản ghi liên quan đến việc chi trả lương và hoa hồng.
  - Biểu đồ package mô tả kiến trúc:
    ![PackageDiagram]([https://planttext.com/api/plantuml/png/P951YW9134NtEKNm07q05s8xin5S23AhmKMeoMXXMIr9McXaJZOBZ-GLhB8LhJQhokCb_52N__DKZSJQVG3GdOyeZJAOjy2uf4wQ473LgV4UQt5RR-oi5GOuaDlH9ad2oj78V1CNrB7W2J3LzvUczpmQooyvNiFVSsRMge-iMlWFY8jcurtXhrYEtd6XtndUO65_ab7jt71_njZpbw7t-5Kr6GGSuoWTeoCeSHQBPCdxe12IME3i3JCbjM_pMfXo_Ca_S0K00F__0m00](https://planttext.com/api/plantuml/png/X5CxJiGm4ErpYj7sst00j6H3WRH8aK2YG2a6PuXC73ko7Q48SJ8AZiGLSCYo9lR6k9nvRzwRZxy-FdV6ehP39x8UMOiDmQRKP4XQj5n9EE18UWDl6RZt-C1bhLuD56HQgthO2-wGLVQUUVfLtmlEph5B7BKI0lB1S4d6m44rd5Lpyfvtn53NS8lIrT7LYTCvYI1wtVL2ZKG-_DV1ZRJKw7CEYlm2zafAObRzrifHjZ1Hz3CoEWRlY0sQst7cByiNQ36eU_8pvPxGKBNiE0XFDagjNfoDOmS_FNgKarkRDMotb-kZN4lCh7Z6QNmq_3Gytagi621zov7OEZBIMON-OpWuXpGul9CqEZoWB13p1fA74Aekj-znEvBrz8c_0G00__y30000))
**Câu 2:** Cơ chế phân tích
  - a. Quản lý thời gian làm việc (Timecard Management)
      Mô tả: Hệ thống cần một cơ chế để quản lý thời gian làm việc cho các nhân viên, bao gồm việc ghi nhận số giờ làm việc, dự án tương ứng và tính toán giờ tăng ca.
      Lý do: Đây là yêu cầu nghiệp vụ cốt lõi của hệ thống để tính toán lương cho nhân viên.
  - b. Tính lương và hoa hồng (Payroll and Commission Calculation)
      Mô tả: Cơ chế tính toán lương cần được thiết kế để đáp ứng nhiều loại nhân viên khác nhau: nhân viên trả theo giờ, nhân viên lương cứng và nhân viên có hoa hồng.
      Lý do: Hệ thống cần tính toán lương chính xác dựa trên loại hợp đồng và các yếu tố khác như hoa hồng và giờ tăng ca.
  - c. Tích hợp với cơ sở dữ liệu dự án (Project Management Integration)
      Mô tả: Hệ thống cần có khả năng tích hợp và truy xuất thông tin từ cơ sở dữ liệu quản lý dự án (DB2) để ghi nhận charge numbers và dự án tương ứng với giờ làm việc.
      Lý do: Đây là yêu cầu nghiệp vụ quan trọng do hệ thống phải tương thích với cơ sở dữ liệu DB2 hiện có mà không được phép thay thế.
  - d. Quản lý phương thức thanh toán (Payment Method Management)
      Mô tả: Hệ thống cần hỗ trợ nhiều phương thức thanh toán, bao gồm nhận trực tiếp, qua bưu điện hoặc chuyển khoản ngân hàng.
      Lý do: Nhân viên có quyền lựa chọn phương thức thanh toán và hệ thống cần xử lý chính xác các thông tin liên quan.
  - e. Quản lý bảo mật (Security Management)
      Mô tả: Bảo mật là cơ chế quan trọng để đảm bảo nhân viên chỉ có quyền chỉnh sửa thông tin chấm công của chính họ, và chỉ có quản trị viên lương có thể thay đổi thông        tin nhân viên.
      Lý do: Đảm bảo tuân thủ các yêu cầu bảo mật trong việc xử lý thông tin nhạy cảm.
  - f. Tích hợp với hệ thống ngân hàng (Banking Integration)
      Mô tả: Hệ thống cần có khả năng kết nối với hệ thống ngân hàng để xử lý các giao dịch chuyển khoản cho nhân viên có yêu cầu trả lương qua ngân hàng.
      Lý do: Đảm bảo lương được thanh toán chính xác và đúng hạn qua các kênh thanh toán đã chọn.
  - g. Tự động hóa quy trình trả lương (Automated Payroll Processing)
      Mô tả: Hệ thống phải tự động chạy quy trình trả lương vào các ngày được chỉ định mà không cần can thiệp thủ công.
      Lý do: Giúp giảm thiểu lỗi và tăng tính hiệu quả trong quy trình trả lương hàng tuần và hàng tháng.
  - h. Báo cáo nhân viên (Employee Reporting)
      Mô tả: Cơ chế tạo báo cáo cho phép nhân viên truy xuất thông tin như tổng số giờ làm việc, số lương đã nhận, số giờ làm việc theo từng dự án, và số ngày nghỉ phép còn       lại.
      Lý do: Giúp nhân viên theo dõi và kiểm soát thông tin cá nhân liên quan đến lương và thời gian làm việc.
**Câu 3:** Phân tích ca sử dụng Select Payment
  a. Xác định các lớp phân tích.
    - Employee(Nhân viên):
        - Thuộc tính:
           + employeeId: ID của nhân viên.
           + name: Tên nhân viên.
           + address: Địa chỉ của nhân viên (dùng cho phương thức nhận qua thư).
        - Phương thức:
           + selectPaymentMethod(): Chọn phương thức thanh toán.
           + provideBankDetails(): Cung cấp thông tin tài khoản ngân hàng (dành cho Direct Deposit).
    - PaymentMethod (Phương thức thanh toán):
        - Thuộc tính:
           + type: Loại phương thức thanh toán (Pick-up, Mail, Direct Deposit).
        - Phương thức:
           + validate(): Xác thực phương thức thanh toán.
    - System (Hệ thống): Hệ thống quản lý thông tin nhân viên và phương thức thanh toán
        - Phương thức:
           + requestPaymentMethod(): Yêu cầu nhân viên chọn phương thức thanh toán.
           + requestMailAddress(): Yêu cầu cung cấp địa chỉ gửi thư (nếu chọn phương thức gửi thư).
           + requestBankDetails(): Yêu cầu cung cấp thông tin ngân hàng (nếu chọn phương thức Direct Deposit).
           + updatePaymentMethod(): Cập nhật phương thức thanh toán của nhân viên trong hệ thống.
    - BankAccount (Tài khoản ngân hàng):
        - Thuộc tính:
           + bankName: Tên ngân hàng.
           + accountNumber: Số tài khoản ngân hàng.
        - Phương thức:
           + validateAccountDetails(): Xác thực chi tiết tài khoản ngân hàng.
  b. Mô tả hành vi thông qua biểu đồ tuần tự (sequence diagram).
    - Dưới đây là mô tả sơ bộ cho biểu đồ tuần tự cho ca sử dụng Select Payment Method:
      ![sequence diagram](https://planttext.com/api/plantuml/png/X991RW8n34NtEOMN8BMmdqL52wZgOYJKgWUmY8T69CxKyImuMnSzKg_G313HGHHsKM8_-p_bv-jxbXH5k-0DhZKAB4Fhuux8c7A2-mTOuIuGQusC6v8ANkcpewJb7chIZsZXZJojrKKsmuQ_Y7rb1S-aCEz4JjrcK75vgdR2_xMTHfNDArX93Ar2auCDLxqUxv3ZFDs89fl97IoSz8yBQcDo2XbTe_FZsv6Bj4ThNIy9FRnm4s6KBuHIcZuXRpDNCowDBszuH2rPyuXzVO-O7Wct5Rwt5fNEPLnJE8_SE0b5mW6G_Ss8RVzjVW400F__0m00)
  c. Xác định nhiệm vụ của từng lớp phân tích.
    - Employee:
        Chọn phương thức thanh toán.
        Nhập thông tin bổ sung (địa chỉ hoặc tài khoản ngân hàng) nếu cần.
    - PaymentMethod:
        Lưu trữ thông tin về phương thức thanh toán đã chọn.
        Cập nhật phương thức thanh toán (nhận trực tiếp, qua bưu điện, hoặc chuyển khoản).
    - BankAccount:  
        Lưu trữ thông tin tài khoản ngân hàng nếu nhân viên chọn phương thức chuyển khoản trực tiếp.
    - PaymentManager:
        Xử lý yêu cầu chọn và cập nhật phương thức thanh toán.
        Lưu trữ và truy xuất phương thức thanh toán hiện tại.
    - Address:
        Lưu trữ địa chỉ gửi phiếu lương nếu nhân viên chọn phương thức nhận qua bưu điện.
  d.  Quan hệ giữa các lớp phân tích.
    - Employee và PaymentMethod:
        Một nhân viên chỉ có một phương thức thanh toán tại một thời điểm (quan hệ 1-1).
    - PaymentMethod và BankAccount/ Address:
        Nếu phương thức thanh toán là Direct Deposit, cần một thông tin BankAccount.
        Nếu phương thức thanh toán là Mail, cần một Address để gửi phiếu lương.
  e. Biểu đồ mô tả lớp phân tích.
      ![ClassDiagram](https://planttext.com/api/plantuml/png/V99BJiCm48RtFeNLLLcaebjMBQKB9AXOS07N7WKBFo9xWXGXJiQ28t459i4sTIXaCydup__Dmv_l7vk88c1l3MFIY1ZvtdR63m3ybN5w6WufSQlu5TSEKze92vI86BHhYrHeKoSvZs10ueCOB3Yy1tpoQdb1eXUl5NlBsEgyiEtq-JXqC7VjEoKG_hIx5kvvAwNl7HQp8-KEPweMtxf3RuyGvfmMSFIw0QJMuaHAvuMrLIe0nSoXSm2SKwJ6OPxhF4tVxBpwrHvXa-rPP9wMSAAbcZEvEntYdOvZ4MD8fdQIftz_XbQ8kpw4UaVLLaPykHsBzO8tpHHgKRt8BBjShUZjP2l_wbBhRDOc2MeMsu1Juztz0W00__y30000) 
**Câu 4:** Phân tích ca sử dụng Maintain Timecard
  a. Xác định các lớp phân tích.
    - Employee: Đại diện cho nhân viên sử dụng hệ thống để nhập và quản lý thời gian làm việc.
    - Timecard: Lớp đại diện cho thông tin thời gian làm việc của nhân viên, bao gồm các thuộc tính như ngày bắt đầu, ngày kết thúc và số giờ làm việc.
    - Project: Lớp đại diện cho các dự án mà nhân viên làm việc, bao gồm số hiệu dự án và thông tin liên quan.
    - TimecardManager: Lớp xử lý logic cho việc lưu trữ, xác thực và cập nhật thông tin thời gian làm việc.
    - Validation: Lớp chịu trách nhiệm kiểm tra các điều kiện hợp lệ cho giờ làm việc và trạng thái của thời gian làm việc.
  b. Mô tả hành vi thông qua biểu đồ tuần tự.
    - Dưới đây là mô tả sơ bộ cho biểu đồ tuần tự (sequence diagram) cho ca sử dụng Duy trì Thời gian làm việc:
    ![SequenceDiagram](https://planttext.com/api/plantuml/png/Z99D3e8m48NtFKKlu0LO61PYt9WO__OZJ4nDQR6Tck3LN7Waho0OAAXOsKqwtxoyUTF7xHvR0aCkbmnIqeOdUI5rYSXOM_79b6z5ZYcOR0aAZcWYliQpGqk-mJw8_b1Dan5umM_yXpWveuBQhRc8puGj99GTFOIlZ3vXIZqdpOjbJH4oujbHHZmTJZ1HL2aij3E3kbruko836XlT1lefXnrit24NOq-u1obUFjuT3methD2gIj0wIM7fkL3Lm7NiYhvPx_hdStGi0Rdg936ghFxiJm000F__0m00)
  c. Xác định nhiệm vụ của từng lớp phân tích.
    - Employee:
        Nhập thông tin thời gian làm việc.
        Chọn số hiệu dự án.
        Nộp thời gian làm việc.
  - Timecard:
        Lưu trữ thông tin về thời gian làm việc của nhân viên.
        Cung cấp thông tin cho các lớp khác về giờ làm việc, ngày bắt đầu và ngày kết thúc.
  - Project:
        Cung cấp thông tin về các dự án để nhân viên có thể chọn.
        Lưu trữ số hiệu dự án và thông tin liên quan.
  - TimecardManager:
      Xử lý logic cho việc tạo, lưu trữ và xác thực thời gian làm việc.
      Cập nhật thông tin thời gian làm việc và kiểm tra điều kiện hợp lệ.
  - Validation:
      Kiểm tra tính hợp lệ của số giờ làm việc.
      Đảm bảo rằng không có vi phạm về giới hạn giờ làm việc.
  d. Xác định một số thuộc tính và quan hệ giữa các lớp phân tích.
  #Thuộc tính của các lớp phân tích:
  - Employee
      employeeId: Mã nhân viên
      name: Tên nhân viên
      email: Địa chỉ email
  - Timecard
      startDate: Ngày bắt đầu
      endDate: Ngày kết thúc
      hoursWorked: Danh sách số giờ làm việc cho từng ngày và số hiệu dự án.
  - Project
      projectId: Số hiệu dự án
      projectName: Tên dự án
  - TimecardManager
      timecardList: Danh sách các thời gian làm việc
  - Validation
      maxHoursPerDay: Giới hạn giờ làm việc mỗi ngày
      maxTotalHours: Giới hạn tổng số giờ làm việc cho kỳ thanh toán
  #Quan hệ giữa các lớp phân tích:
  - Employee và Timecard:
      Một Nhân viên có thể có nhiều Timecard (quan hệ 1-n).
  - Timecard và Project:
      Một Timecard có thể liên kết với nhiều Project (quan hệ n-n), do đó có thể cần một lớp liên kết như TimecardProject để lưu thông tin về số giờ làm việc cho từng dự án.
  - TimecardManager:
      Có thể tương tác với cả Timecard và Validation để xử lý và xác thực thông tin.
  e. Biểu đồ lớp mô tả phân tích:
    ![ClassDiagram](https://planttext.com/api/plantuml/png/R5B1JiGW5Bpp5IyzwQ47hyQOFQo99chsiD7ps_9IKGeDqCQDySiy-4d-Wj02RRVR2s5cOEPD-VlvtLY7ndMDPAoIQ2tSDQtKHoBuOk2_4YW23nokGIWNOOKDUS0w8rITfIZa4WGWvSZSwyxOYqlFzLhmoDZkq0Yt5mrLQFZ4VgSiYSfPXh1RTC4vBCbNyJNu5YnVjVcWUN20hkLUT3uGzdGcnixeTwfSJj6E-vD28lgywWMW9XVl62qVXNNhAPzGOKqcsxY81tKyT9Eqj_7cof0VPb5XsaH5ZrBmKyr1QqcefWmleqfebUqR_1nAsf7Pud4nggVssg4S-4MvoMsgTsQLdrPnLK1PGg6AAMt-rm6DP2oDdJRawTMv6JSDmzZ6lutmkly1003__mC0)
**Câu 5:** Hợp nhất kết quả phân tích
  a. Giới thiệu:
    - Select Payment Method: Cho phép nhân viên chọn phương thức thanh toán, bao gồm nhận trực tiếp, qua bưu điện, hoặc chuyển khoản ngân hàng.
    - Maintain Timecard: Cho phép nhân viên nhập và quản lý bảng chấm công, bao gồm thông tin số giờ làm việc và dự án tương ứng.
  b. Phân tích yêu cầu:
    - Ca sử dụng 1: Select Payment Method
      + Mô tả:
        - Nhân viên có thể chọn phương thức thanh toán bao gồm nhận phiếu lương trực tiếp, qua bưu điện hoặc chuyển khoản trực tiếp vào tài khoản ngân hàng.
      + Yêu cầu chức năng:
        - Nhân viên chọn một trong ba phương thức thanh toán.
        - Hệ thống yêu cầu thông tin bổ sung tùy vào lựa chọn (địa chỉ hoặc tài khoản ngân hàng).
        - Hệ thống cập nhật phương thức thanh toán vào hồ sơ nhân viên.
    - Ca sử dụng 2: Maintain Timecard
      + Mô tả:
        - Nhân viên có thể nhập và quản lý bảng chấm công cho kỳ lương hiện tại, bao gồm việc ghi nhận số giờ làm việc theo từng dự án.
      + Yêu cầu chức năng:
        - Hệ thống hiển thị bảng chấm công hiện tại hoặc tạo bảng chấm công mới nếu chưa có.
        - Nhân viên nhập số giờ làm việc theo từng dự án và ngày tương ứng.
        - Hệ thống xác thực tổng số giờ làm việc và lưu lại bảng chấm công.
  c. Phân tích lớp:
    - Các lớp phân tích chính:
      + Employee (Nhân viên): Đại diện cho nhân viên sử dụng hệ thống. Nhân viên có thể chọn phương thức thanh toán và nhập bảng chấm công.
      + PaymentMethod (Phương thức thanh toán): Đại diện cho các phương thức thanh toán nhân viên có thể chọn, bao gồm thông tin về nhận trực tiếp, qua bưu điện hoặc chuyển         khoản ngân hàng.
      + BankAccount (Tài khoản ngân hàng) và Address (Địa chỉ): Lưu trữ thông tin bổ sung nếu phương thức thanh toán yêu cầu.
      + Timecard (Bảng chấm công): Lưu trữ thông tin về số giờ làm việc của nhân viên trong kỳ lương hiện tại.
      + Project (Dự án): Lưu trữ thông tin về các dự án mà nhân viên làm việc và liên kết với số giờ làm việc trong bảng chấm công.
      + TimecardManager và PaymentManager: Quản lý các thao tác liên quan đến bảng chấm công và phương thức thanh toán.
    - Biểu đồ lớp tổng hợp:
      ![ClassDiagram](https://planttext.com/api/plantuml/png/V5HBJiCm4Dtd55PNi6W5MrOjBH98j69HYRKRZrfJVoBRgHGXJiQ28t459edjnav4DXFFFC-Rpqj-lt-Mrb7ZQYcAeXJKMl8aAw4R0F9P47pc1BpZXP47mfNpRaKbeCCwmzKnGYaNgPCG2m9AzqOR2SfjmPqqkxb5q4LpvY4O0FEiQsFpYAqFahizbr1ICxZt5SfDyiQQPNVSDnNarTGLemxoCcAwHwhEgxBKjN8nsG5zkubkQO_RrV809kSvWcjpRS3XIFgsV3nohHWpW3RmO1p0vImbTqtkgpHkJQmr6xM7j3xj96MO5bNqY3K7vceun5Tkso9QuvFA3kxlvXj2ndLjJBhRP2jN-h37GSielWqk1E-q9kX8iR7prEhZNPipj4BSqYhPwBHww0McD6Fq1qhosdv_pWJklUFDTptx73rbDwjHb_cKdVUF1rmQm1OIbOU3Hroeu2p77BGMG5NB7B_QsVsCpEUTIPUGVYW1ThTOuDj0zV_YlBIAJ4O8IBacouaTHHNCL1z4uyTPvBF3SBnNB54NxP_g3m00__y30000)
  d. Biểu đồ tuần tự hợp nhất:
    - Biểu đồ tuần tự cho quy trình chọn phương thức thanh toán (Select Payment Method):
      ![Sequence Diagram](https://planttext.com/api/plantuml/png/X991RW8n34NtEOMN8BMmdqL52wZgOYJKgWUmY8T69CxKyImuMnSzKg_G313HGHHsKM8_-p_bv-jxbXH5k-0DhZKAB4Fhuux8c7A2-mTOuIuGQusC6v8ANkcpewJb7chIZsZXZJojrKKsmuQ_Y7rb1S-aCEz4JjrcK75vgdR2_xMTHfNDArX93Ar2auCDLxqUxv3ZFDs89fl97IoSz8yBQcDo2XbTe_FZsv6Bj4ThNIy9FRnm4s6KBuHIcZuXRpDNCowDBszuH2rPyuXzVO-O7Wct5Rwt5fNEPLnJE8_SE0b5mW6G_Ss8RVzjVW400F__0m00)
    - Biểu đồ tuần tự cho quy trình duy trì bảng chấm công (Maintain Timecard):
      ![Sequence Diagram](https://planttext.com/api/plantuml/png/Z95B2i8m48RtEKKku0Mwa88MtBZnjH_RKGRog9E9qBEvy4XUGOkq5gsXkq2--VFDdyVjdWS1bcYDWb8ywyBMnZU8IdKdFPlh7LaiWQirE3WZPtg3buX1-WlrHGo7MbgOy8g_-9zmYUoIsPrSffSKQWFDXqwB5qvU2IiVEQITztK5CjLu2yFbqWRRUBGqjRa361ht62rZuTs9sFRq-x4Go3kbSdHL-z5F0000__y30000)
  e. Mối quan hệ giữa các lớp:
    - Employee: Lớp Employee tương tác với cả hai chức năng Select Payment Method và Maintain Timecard. Nhân viên có thể chọn phương thức thanh toán hoặc quản lý bảng chấm        công của họ.
    - PaymentMethod: Lớp PaymentMethod lưu trữ thông tin về cách thức nhân viên nhận lương và tương tác với lớp PaymentManager để cập nhật thông tin thanh toán.
    - Timecard: Lớp Timecard lưu trữ thông tin về số giờ làm việc và dự án tương ứng, tương tác với lớp TimecardManager để xác nhận và lưu bảng chấm công.
    - PaymentManager và TimecardManager: Cả hai lớp này quản lý các hoạt động chính của hệ thống liên quan đến thanh toán và bảng chấm công.
