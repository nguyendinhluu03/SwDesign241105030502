#4451050894_NguyenDinhLuu
#Lab2
1. Phân tích ca sử dụng Create Administrative Report:
  a. Xác định các lớp phân tích:
    - Payroll Administrator: Đại diện cho người dùng chính của hệ thống trong Use Case này.
    - ReportRequest: Đại diện cho yêu cầu tạo báo cáo, bao gồm các thông tin về loại báo cáo, khoảng thời gian, và nhân viên.
    - ReportGenerator: Thực hiện chức năng chính là tạo báo cáo dựa trên yêu cầu đã được cung cấp.
    - Report: Đại diện cho kết quả của việc tạo báo cáo, bao gồm dữ liệu cần thiết theo tiêu chí đã cung cấp.
    - FileManager: Xử lý việc lưu trữ báo cáo xuống hệ thống nếu được yêu cầu.
  b. Mô tả hành vi thông qua biểu đồ tuần tự (sequence diagram):
    - Dưới đây là mô tả sơ bộ cho biểu đồ tuần tự cho ca sử dụng Create Administrative Report:
      ![SequenceDiagram](https://planttext.com/api/plantuml/png/d5DBReCm4Dtx5BCCKde15bMG-b4NhL3Q2qpjIMh9sDIUHE9iNVH8lK9j0m4aeahr0eQPUS_p_CpFr_SkC7e-DKQWPEUXniuxOohLQAi3Uqn9351NeesDMkeMBSEUMkTvJvyd2hnIUIHB6RjIMwGUjA5dj7WaBqHTmStjahi4tmTzTkFpwwrhQGllTDJs3Zc6PDKGDArn7T4BDXGAiU1Q8J-ZqIe2d-p1RGg1XY65e4DV4X3N5PABnXAafqZoln6d7Iw4qnuZzKOwosHvEtndgZasGUgg1AL3Qx0RHYb4Raco1cDXwQpyS2vG07OGy4ovEwtUYPavPQuFj8UOJzDl8KKryaTnGSumSna9FOdu4vQanEw3zirhGlQDP09T4Q9SL64TBsLCPpFE4Sz7ebSZeLKYauwcQvjjXyYehNJHAM9QlmIpqxxttlb8cUXsyP5-fry0003__mC0)
  c. Nhiệm vụ của từng lớp phân tích:
    - Payroll Administrator: Gửi yêu cầu, cung cấp tiêu chí cho báo cáo và quyết định có lưu báo cáo hay không.
    - ReportRequest: Thu thập tiêu chí cho báo cáo và xác nhận dữ liệu đầu vào trước khi chuyển yêu cầu cho ReportGenerator.
    - ReportGenerator: Tạo báo cáo dựa trên thông tin từ ReportRequest và trả về một đối tượng Report.
    - Report: Lưu trữ kết quả của báo cáo, bao gồm dữ liệu về tổng số giờ làm việc hoặc tổng lương đến thời điểm hiện tại.
    - FileManager: Xử lý việc lưu báo cáo xuống hệ thống khi được yêu cầu.
  d. Một số thuộc tính và quan hệ giữa các lớp phân tích:
    - Các thuộc tính:
        + ReportRequest
            reportType: String (kiểu báo cáo)
            beginDate: Date (ngày bắt đầu)
            endDate: Date (ngày kết thúc)
            employeeNames: List<String> (danh sách tên nhân viên)
        + Report
            content: String (nội dung của báo cáo)
            createdDate: Date (ngày tạo báo cáo)
        + FileManager
            fileName: String (tên tệp lưu báo cáo)
            filePath: String (đường dẫn lưu báo cáo)
    - Quan hệ giữa các lớp:
        + Payroll Administrator có quan hệ kích hoạt với ReportRequest.
        + ReportRequest có quan hệ sử dụng với ReportGenerator để tạo báo cáo.
        + ReportGenerator tạo một đối tượng Report và trả về.
        + Report có thể được lưu bởi FileManager khi Payroll Administrator yêu cầu.
  e. Biểu đồ mô tả lớp phân tích:
    ![ClassDiagram](https://planttext.com/api/plantuml/png/T55B3e8m5Dpt52nrmHKC9aRZGaE85tZ20vkK5ji72J6Up8L7yWe2BJy_tSrqfc_UzFLu1eP0KvaB5WimnWkXrag8TP9poGrf8AMz6_FQe_5Qeg482wLfiRIaWGe7vixSCvQ9hC7vVTsHfxf0Yy-OSRa1SX1bCW5v8LIDU8GSZPrKWU198zZBL7tFsg74MTfOOoF-5wtF52j9ACc1pc9J3Fej5tW02HdsJ_jfGxN1HXG2NSO-MeiT-RDEtr_D2sBpkiRxOIdskUIeOTE04pfe-cp_zGq00F__0m00)
2. Phân tích ca sử dụng Create Employee Report:
  a. Xác định các lớp phân tích:
    - Employee: Đại diện cho nhân viên trong hệ thống.
    - Report: Đại diện cho các loại báo cáo mà nhân viên có thể tạo.
    - ProjectManagementDatabase: Cơ sở dữ liệu quản lý dự án, nơi lưu trữ thông tin dự án và mã số charge.
    - ReportStorage: Quản lý việc lưu trữ các báo cáo đã tạo.
  b. Mô tả hành vi thông qua biểu đồ tuần tự (sequence diagram):
    - Dưới đây là mô tả biểu đồ sequence cho ca sử dụng Create Employee Report:
      ![SequenceDiagram](https://planttext.com/api/plantuml/png/X591KiCm3Bpd5Ne0VA07BgK31-WmX1dEQhEKG6m5MSbCtiQ19_45dAIXay4DlbYsTbVIsj-VNnjNLz81T7b5UHSCRaMF-6WGBEwrgD5QmLQApyPyZvnO2Mnfq9ApbEw3IbiMcB1FNOqBoerZVCqMuuqlXYZZAgR5kA9RQJJGi-Wx2deH9Uvbth2tZE8wjNIylMVF1pXuYqAyup3qQ5gY1QrVMG-WRUDsq308dAND3R56VOg-PCaCFg2NJ9cZuOkatJVmqEZGqSF1g9pRt_EvAbDF9d_WIoDisO4uligTxCS_yDyOQSQfnbWuDz7ezshMJ3_p3m000F__0m00)
  c. Nhiệm vụ của từng lớp phân tích:
    - Employee:
        + Tương tác với hệ thống để yêu cầu tạo báo cáo.
        + Cung cấp thông tin cần thiết cho hệ thống để tạo báo cáo.
    - Report:
        + Xử lý thông tin đầu vào từ nhân viên.
        + Tạo báo cáo dựa trên thông tin đầu vào.
        + Lưu báo cáo nếu yêu cầu.
    - ProjectManagementDatabase:
        + Cung cấp danh sách charge numbers khi nhân viên chọn báo cáo liên quan đến dự án.
        + Truy xuất thông tin liên quan đến dự án khi cần thiết.
    - ReportStorage:
        + Lưu trữ báo cáo theo yêu cầu của nhân viên.
        + Xác nhận tên và vị trí lưu trữ.
  d. Một số thuộc tính và quan hệ giữa các lớp phân tích:
    - Các thuộc tính:
        + Employee:
              employeeId: ID của nhân viên
              name: Tên nhân viên
              role: Vai trò (ví dụ: nhân viên, quản lý)
        + Report:
              reportType: Loại báo cáo (ví dụ: "Total Hours Worked", "Total Pay Year-to-Date")
              startDate: Ngày bắt đầu
              endDate: Ngày kết thúc
              chargeNumber: Mã số dự án (nếu báo cáo liên quan đến dự án)
              reportData: Dữ liệu báo cáo (có thể là một danh sách hoặc bảng)
        + ProjectManagementDatabase:
              projects: Danh sách các dự án (bao gồm charge numbers)
        + ReportStorage:
              storagePath: Đường dẫn lưu trữ báo cáo
    - Quan hệ giữa các lớp:
        + Employee sử dụng Report để tạo báo cáo.
        + Report yêu cầu thông tin từ ProjectManagementDatabase nếu báo cáo liên quan đến dự án.
        + Report có thể được lưu trữ thông qua ReportStorage nếu nhân viên yêu cầu.
        + ProjectManagementDatabase không có mối quan hệ trực tiếp với Employee, nhưng cung cấp dữ liệu cần thiết để Report có thể tạo báo cáo.
  e. Biểu đồ mô tả lớp phân tích:
    ![ClassDiagram](https://planttext.com/api/plantuml/png/R99DJiGm38NtEKMMiEW5AZGQmR100ZHYk41ehKvHanJRhJH2d8m5H-8AvA-Hcj9DPB_4xxFTt--VFR52dlGWca4HoNiz3lO283-5T5yb8IKUMbdB4sDlkgGOfQ7CeHsAd9G87nCGly1eaQ-kdJpRlXLV8bb68HjY25yluwPuG3qeze8_5aBJRfFDMM47pvD-0zn01WTtMPMe7HX0LwHaZIgfUQFaBevetw7X9sLK1neC7svpIsFKo3rwx8blekSkpyU5CCDTGAPGUtMjcDI9BJgFN9rYV5HyBllnn2lMlDwgsYs3hvSDaKWPB_xNJvrPAGruzMIDLmTt4dkt7_z__G400F__0m00)        
3. Phân tích ca sử dụng Login:
  a. Xác định các lớp phân tích:
    - User: Đại diện cho người dùng trong hệ thống, người sẽ thực hiện việc đăng nhập.
    - LoginManager: Xử lý quá trình đăng nhập, kiểm tra thông tin đăng nhập và quyết định xem người dùng có thể đăng nhập hay không.
    - AuthenticationService: Quản lý việc xác thực người dùng trong hệ thống.
  b. Mô tả hành vi thông qua biểu đồ tuần tự (sequence diagram):
    - Dưới đây là mô tả biểu đồ sequence cho ca sử dụng Login:
      ![SequenceDiagram](https://planttext.com/api/plantuml/png/f90z2W8n48Nxd69ABSH-2q5a1S45OT5-ICOr42SmITR3MNWahs2M9I3-DKxvvhtv7dE_tlQ116OBsFhESeEC7Ka5DSSi3pl6Cm6oWHs6SF5YrBDpI2vJF157gp5Qpor9RpLLS41d3KRwSWLT72sm4Z937brGaEVZlVUARTAQmXXvhJGWgr4jlcDoYbmWs73_3tQDrYMX7zXQn0iqcPbrc1HUUSEyl62gY8rw0000__y30000)
  c. Nhiệm vụ của từng lớp phân tích:
    - User:
          + Cung cấp thông tin đăng nhập (tên và mật khẩu) cho hệ thống.
    - LoginManager:
          + Kiểm tra thông tin đăng nhập của người dùng.
          + Thông báo kết quả (thành công hay thất bại).
    - AuthenticationService:
          + So sánh tên và mật khẩu do người dùng cung cấp với thông tin trong cơ sở dữ liệu.
          + Xác nhận nếu thông tin hợp lệ.
  d. Một số thuộc tính và quan hệ giữa các lớp phân tích:
    - Các thuộc tính:
          + User:
              username: Tên đăng nhập của người dùng
              password: Mật khẩu của người dùng
          + LoginManager:
              loginStatus: Trạng thái đăng nhập (đã đăng nhập/thất bại)
          + AuthenticationService:
              userDatabase: Cơ sở dữ liệu chứa thông tin tài khoản người dùng (tên đăng nhập và mật khẩu).
    - Quan hệ giữa các lớp:
          + User tương tác với LoginManager để thực hiện quá trình đăng nhập.
          + LoginManager sử dụng AuthenticationService để kiểm tra thông tin đăng nhập.
          + AuthenticationService so sánh thông tin đăng nhập với dữ liệu trong cơ sở dữ liệu.
  e. Biểu đồ mô tả lớp phân tích:
      ![ClassDiagram](https://planttext.com/api/plantuml/png/Z54nRiCm3Dpr2euk47_0A88axTXCHXx0MeGZG9PSaNA6eY_hq2Vb2v4I6wxX3jKYYJeUxqxNxvyT2mQ9dLMDHMOuCGNuL91M2J5T77O45TGIZ6l7Uf-G5n_qiWv0JYYy1DBfOD1oyPGGWpTQVQcH_ystnXtHOVjhZit5Mb0YfuQ3zvRGZPm3MgDHwDvOh1HjrcBMG_THpbbIWsAygoaCfg65orSKV4VEl4VidoVknxuTfU1CG_zMChb9OkxPbkLs6KBrY8sXcODJ2qHk-Tj21O4-8h7mb5DwL3joEl_e3G00__y30000)
4. Phân tích ca sử dụng Maintain Employee Information: 
5. Phân tích ca sử dụng Maintain Purchase Order:
6. Phân tích ca sử dụng Run Payroll:
