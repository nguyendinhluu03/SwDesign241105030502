#Lab1
Câu 1: Phân tích kiến trúc
  - Kiến trúc dịch vụ: kiến trúc 4 lớp
  - Giải thích lý do lựa chọn:
     + Tính tách biệt mỗi lớp, giúp quản lý và phát triển hệ thống dễ dàng.
     + Khả năng mở rộng dễ dàng bổ sung các tính năng mới mà không làm gián đoạn các phần khác của hệ thống.
     + Bảo trì và kiểm soát lỗi tốt.
     + Hệ thống dễ dàng tích hợp với các dịch vụ và hệ thống bên ngoài.
  - Ý nghĩa:
     + Presentation Layer: Kết nối giữa người dùng và hệ thống, cung cấp giao diện thân thiện.
     + Business Layer: Thực hiện quy trình nghiệp vụ chính, đảm bảo tính chính xác và đáng tin cậy trong việc tính toán lương và xử lý hoa hồng.
     + Service Layer: Quản lý giao tiếp giữa lớp nghiệp vụ và lớp truy cập dữ liệu
     + Data Access Layer: Gíup truy cập và quản lý cơ sở dữ liệu, thực hiện lưu trữ và truy xuất thông tin.
  - Biểu đồ package mô tả kiến trúc:
    ![PackageDiagram](https://planttext.com/api/plantuml/png/P951YW9134NtEKNm07q05s8xin5S23AhmKMeoMXXMIr9McXaJZOBZ-GLhB8LhJQhokCb_52N__DKZSJQVG3GdOyeZJAOjy2uf4wQ473LgV4UQt5RR-oi5GOuaDlH9ad2oj78V1CNrB7W2J3LzvUczpmQooyvNiFVSsRMge-iMlWFY8jcurtXhrYEtd6XtndUO65_ab7jt71_njZpbw7t-5Kr6GGSuoWTeoCeSHQBPCdxe12IME3i3JCbjM_pMfXo_Ca_S0K00F__0m00)
Câu 2: Cơ chế phân tích
  - Đề xuất cơ chế và giải thích lý do:
    + Xác thực người dùng:
        Giải thích: Đảm bảo nhân viên hợp lệ mới có quyền truy cập vào hệ thống và thục hiện quyền chỉnh sửa.
    + Phân quyền:
        Giải thích: Đảm bảo nhân viên chỉ có quyền truy cập và chỉnh sửa thông tin mà họ có quyền.
    + Quản lý dữ liệu nhân viên:
        Giải thích: Quản lý thông tin nhân viên.
    + Tính toán lương:
        Giải thích: Cần có cơ chế tự động tính toán lương cho từng nhân viên dựa trên giờ làm việc và doanh số bán hàng.
    + Đồng bộ hóa dữ liệu:
        Giải thích: Đảm bảo rằng dữ liệu trên các máy tính cá nhân của nhân viên được đồng bộ với cơ sở dữ liệu trung tâm.
Câu 3:  Phân tích ca sử dụng Select Payment
Câu 4: Phân tích ca sử dụng Maintain Timecard
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
Câu 5: Hợp nhất kết quả phân tích

