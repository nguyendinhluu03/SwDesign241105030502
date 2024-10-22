#Lab1
Câu 1: Phân tích kiến trúc
Câu 2: Cơ chế phân tích
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
    ![SequenceDiagram](https://planttext.com/api/plantuml/png/R5B1JiGW5Bpp5IyzwQ47hyQOFQo99chsiD7ps_9IKGeDqCQDySiy-4d-Wj02RRVR2s5cOEPD-VlvtLY7ndMDPAoIQ2tSDQtKHoBuOk2_4YW23nokGIWNOOKDUS0w8rITfIZa4WGWvSZSwyxOYqlFzLhmoDZkq0Yt5mrLQFZ4VgSiYSfPXh1RTC4vBCbNyJNu5YnVjVcWUN20hkLUT3uGzdGcnixeTwfSJj6E-vD28lgywWMW9XVl62qVXNNhAPzGOKqcsxY81tKyT9Eqj_7cof0VPb5XsaH5ZrBmKyr1QqcefWmleqfebUqR_1nAsf7Pud4nggVssg4S-4MvoMsgTsQLdrPnLK1PGg6AAMt-rm6DP2oDdJRawTMv6JSDmzZ6lutmkly1003__mC0)
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
  #Thuộc tính của các lớp phân tích
Câu 5: Hợp nhất kết quả phân tích

