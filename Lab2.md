**#4451050894_NguyenDinhLuu
#Lab2**
**I. Tiến hành phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System:**
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
  a. Xác định các lớp phân tích:
    - PayrollAdministrator: Đại diện cho quản trị viên tiền lương, người thực hiện các thao tác duy trì thông tin nhân viên.
    - Employee: Đại diện cho một nhân viên trong hệ thống.
    - EmployeeManager: Quản lý các thao tác thêm, cập nhật, và xóa thông tin nhân viên trong hệ thống.
    - PayrollSystem: Hệ thống tính lương, nơi các thay đổi về thông tin nhân viên sẽ được thực hiện.
  b. Mô tả hành vi thông qua biểu đồ tuần tự (sequence diagram):
    - Dưới đây là biểu đồ sequence cho ca sử dụng Maintain Employee Information.
      ![Add an Employee](https://planttext.com/api/plantuml/png/UhzxVq1YPL5-JevZIcvcNcPnIL5YINwHWgwTWcjkGKv-PMggRs9UOdfgaPL2K6fXQMfnYO9ZIWfSaWjD5KWZDWCHkc4Q53ppqlABSXDBClFpk8XsGq1HVbbcIYfsKx2u1IPafU1Sb9fOWgGnA3KvloY55FUNb1Rb8LdimWK0003__mC0)
      ![Update an Employee](https://planttext.com/api/plantuml/png/UhzxVq1YPL5-JevZIcvcNcPnIL5YINwHWgwTWcjkGKv-PMggRs9UOdfgaPL2K6fXQMfnYK9eGKfYIIfSdWjD8KWlDZCH1i0qA7YwS15jUq1HVbbcIYgAPYmsmuH0jfKKPQQM8Ul8IyiloaqioSpF8zvUDD-Y68BNVgZ6eDJa_A8KBW00003__mC0)
      ![Delete an Employee](https://planttext.com/api/plantuml/png/d8zH3i5048RVznHp0HVm896Mn8D4z0IJziV6x2xJ9UdPF3YIAr0K5QInZpFxpVV_fyDnnfK6aM7XhBTbL8v1gJUWaTj8g80fUrv2-pJ7TeSoKWf1n6DltZxMxAURpmCDG9FKTBRFDEnjWHRymToCQbjKY_qhuHT17KSRVFVGIV0Bg-xMkYPPOdi8GvVNkSYTlK8_2qnPrtH9_5H_GUxgh2eZN9-oV8LY9w2nzIpDra1AKC8-X_oNkuN25-OC003__mC0)
  c. Nhiệm vụ của từng lớp phân tích:
    - PayrollAdministrator:
          + Cung cấp yêu cầu để thêm, cập nhật hoặc xóa thông tin nhân viên.  
    - Employee:
          + Quản lý thông tin của nhân viên.
          + Cập nhật các thông tin khi được yêu cầu.
    - EmployeeManager:
          + Thêm nhân viên mới vào hệ thống và tạo ID duy nhất cho nhân viên.
          + Cập nhật thông tin nhân viên dựa trên ID.
          + Xóa nhân viên khỏi hệ thống sau khi nhận xác nhận.
    - PayrollSystem:
          + Quản lý quá trình thanh toán lương và cập nhật các thay đổi nhân sự.
          + Tạo bảng lương cuối cùng cho nhân viên bị xóa.
  d. Một số thuộc tính và quan hệ giữa các lớp phân tích:
    - Các thuộc tính:
          + PayrollAdministrator:
                adminId: ID của quản trị viên
                name: Tên của quản trị viên
          + Employee:
                employeeId: ID của nhân viên
                name: Tên nhân viên
                type: Loại nhân viên (theo giờ, hưởng lương cố định, hưởng hoa hồng)
                mailingAddress: Địa chỉ thư từ
                socialSecurityNumber: Số an sinh xã hội
                standardTaxDeductions: Khấu trừ thuế tiêu chuẩn
                otherDeductions: Khấu trừ khác (401k, y tế)
                phoneNumber: Số điện thoại
                hourlyRate: Mức lương theo giờ (cho nhân viên theo giờ)
                salary: Lương (cho nhân viên hưởng lương và hoa hồng)
                commissionRate: Tỷ lệ hoa hồng (cho nhân viên hoa hồng)
                hourLimit: Giới hạn giờ làm việc
          + EmployeeManager:
                employeeRecords: Danh sách các hồ sơ nhân viên
    - Quan hệ giữa các lớp phân tích:
          + PayrollAdministrator tương tác với EmployeeManager để thực hiện các thao tác thêm, cập nhật hoặc xóa nhân viên.
          + EmployeeManager quản lý các Employee và có trách nhiệm lưu giữ thông tin nhân viên, đồng thời thực hiện thêm, cập nhật hoặc xóa.
          + Employee chứa tất cả các thông tin của nhân viên.
          + PayrollSystem cập nhật thông tin nhân sự và tạo bảng lương cuối cùng khi cần.
  e. Biểu đồ mô tả lớp phân tích:
      ![ClassDiagram](https://planttext.com/api/plantuml/png/Z5DPJiCm4FtFAVpPIkG25QfQgLH2AWYrS8317bfBNi9uWeWG9-E38t45dEBGR2pvovltPdt-U7jV10RYqffC6WX1t415tfYbijhfm0JiIRna8dwvW1gzL68cTapQxHFim68N4uBmiSJ0IwKkR65yXJYPHiwJrwhBk2iKCFv1Mg71CT9hbjfkGj-jOWB-qsqkk2e6c0Ljub-SW31Mw4M3bnhC3cL9cglhqjuZ3JWCJW6fMtXUeIebQ-_gH6lZWHF7ym7fnsXny0x7anzyIQRQnjtrD04CKDK3fRTMXn1BZ2ZgL1jjDNTm8ShZQIxTWoSBTNk_BFuA7EoH1llVelIawhasqKxd3NsUIa3B7ura1GpJlf_AharEvprB8TN8MkvHNTkSHCCvakztLM2qQGeXWZp4qnXSQmScKIOZrchd6tr1UJuVh6hMk3lKNdEC3fp4h4zhIwF67k4mIkiECKkR2QBumhC5EbK_zKy0003__mC0)
5. Phân tích ca sử dụng Maintain Purchase Order:
  a. Xác định các lớp phân tích:
    - CommissionedEmployee: Đại diện cho nhân viên hoa hồng, người thực hiện các thao tác duy trì đơn đặt hàng để nhận hoa hồng.
    - PurchaseOrder: Đại diện cho đơn đặt hàng của một khách hàng được ghi lại bởi nhân viên hoa hồng.
    - PurchaseOrderManager: Quản lý các thao tác thêm, cập nhật, và xóa đơn đặt hàng trong hệ thống.
    - System: Đại diện cho hệ thống chính xử lý xác thực và điều hướng các thao tác.
  b. Mô tả hành vi thông qua biểu đồ tuần tự (sequence diagram):
    - Dưới đây là các biểu đồ sequence cho từng thao tác chính trong ca sử dụng Maintain Purchase Order.
      ![Create a Purchase Order](https://planttext.com/api/plantuml/png/UhzxltD-RcvcSN5cVbvgYcjkGKv-PMggWgwTGa1fKN96Od6gVr5AQf5lObvYUcgHbK9GQc5fQd69WdDHQc99AboH0bWL5pOz8BEmsO4m2zKG1S-yjFoYtCGIe6ekqXmNK9HVbfc2xYeK0t6v44NS2hltW0vEpYzA8TcN9QL5UHXkSk420000__y30000)
      ![Update a Purchase Order](https://planttext.com/api/plantuml/png/b95DRi9038NtSmfVe1TWKQa2L6M1GA2ojsBJZZG_gJs9bBDrqIDn1IP0Iq09KcRfyVly_7py-Pr7xwsgZO5fwIiNMsPuUOLDBUKNAg-5M5OOy9Db1bl-hbaJV5I4YV-RuDnbXZGTQsZ6ZNKFWM9XfddQI6miFPhfE6D-TgqczZFOizX32szboQg0WM2NCDLgq2NOexFK_xjWhSAwuc0WlmjdtDbL_2uO4jDPCcRfhjvbayHoynViC-Lmk0khbSFsyK8TQ5gwWvU68XoYU4mPCcMjAspBPHGox3Al24q_w2WmTr6PUePlCJ_VTIcIvQkCoUCD1p8d0000__y30000)
      ![Delete a Purchase Order](https://planttext.com/api/plantuml/png/f99DJiCm48NtFiLSW0jqWOII2dLHjQ9IzrOy1Kl-2JDEf9oD1KVY2jXEQPEIL4HuwPdtpVCRVtry5jvQpQozGxMsjV4T8ZmymhwXwaqoxaWXRQMJhqWhUC7t1Zb0YGO3NfeWTuafJM9DpRYonX3Ob6APfptvLgjRCuapv-VGSK2xWYEIFdNmL5N83D8fE0GP6XRI13XAezMmrcCrmwv69o2UdZFlx2n-9ka2gYoPipIwJza4qjZ-17jFEHrkgRasihlTq79GuTr9a-qt7ciPaV8P5J1VfxDiTsV8HVtdUAmVXOCcFh6GhaBpJqE_6EYKoFYDQuTVmXCKnZEgWOthXxY_bJLHb6yZ9auLQS8t0000__y30000)
  c. Nhiệm vụ của từng lớp phân tích:
    - CommissionedEmployee:
          + Cung cấp yêu cầu để tạo, cập nhật hoặc xóa đơn đặt hàng.
    - PurchaseOrder:
          + Quản lý thông tin của đơn đặt hàng.
          + Cập nhật thông tin đơn hàng khi được yêu cầu.
    - PurchaseOrderManager:
          + Thêm đơn đặt hàng mới vào hệ thống và tạo ID duy nhất cho đơn hàng.
          + Cập nhật thông tin đơn đặt hàng dựa trên ID.
          + Xóa đơn đặt hàng khỏi hệ thống sau khi nhận xác nhận.
    - System:
          + Xác thực quyền truy cập của Commissioned Employee vào đơn đặt hàng.
  d. Một số thuộc tính và quan hệ giữa các lớp phân tích:
    - Các thuộc tính:
          + CommissionedEmployee:
               employeeId: ID của nhân viên
               name: Tên của nhân viên
          + PurchaseOrder:
                orderId: ID của đơn đặt hàng
                customerContact: Thông tin liên hệ khách hàng
                billingAddress: Địa chỉ thanh toán của khách hàng
                products: Danh sách sản phẩm được mua
                date: Ngày đặt hàng
                status: Trạng thái của đơn đặt hàng (mở/đóng)
          + PurchaseOrderManager:
                purchaseOrders: Danh sách các đơn đặt hàng
          + System:
    - Quan hệ giữa các lớp:
          + CommissionedEmployee tương tác với PurchaseOrderManager để thực hiện các thao tác tạo, cập nhật hoặc xóa đơn đặt hàng.
          + PurchaseOrderManager quản lý các PurchaseOrder và chịu trách nhiệm duy trì các thông tin liên quan đến đơn đặt hàng.
          + System xác thực quyền truy cập của CommissionedEmployee vào đơn đặt hàng và đảm bảo rằng chỉ những đơn hàng thuộc về họ và đang mở mới được sửa hoặc xóa.
  e. Biểu đồ mô tả lớp phân tích:
    - Dưới đây là biểu đồ lớp của ca sử dụng Maintain Purchase Order.
      ![ClassDiagram](https://planttext.com/api/plantuml/png/X5DBQiCm4Dtx55esq5mWb93WT65eQI7q01DfaWhqSJMZW2azMHSzKgzGsL4I9tQ9DqBptepUUv9_ltyMn10uMbD80qIYzDPg8kqTgaTR6zyWYiz2f6ygC1Sg9MPYpK6xNKOSMBoi2H7m8o9n6H0ONuB2S3T9dBtNwfBnLgiRZ1KQ732-YgpvDGRv3dJ0Js9zknigbP7OMmobTmoIh-6DDYRjbae5JAElq3fu5IMtzITD_700vnbjNIHabPPSIU5ofEjWOkUtSbiVB72A-fQdPt2mwrch--19p4NBF9ybU-btYIHrC1bNr6DLwZuNrR6XTokgTnsPFdImReZHPir2x37eRREKCiLwFkFyeje16-yDWcjdZBx3wNG-7ipi-518MD2EqO6JM8no1qDIj-qm-hyXcvaTR6Wa0PsJOe5EjN_F7m000F__0m00)
6. Phân tích ca sử dụng Run Payroll:
  a. Xác định các lớp phân tích:
    - PayrollSystem: Đại diện cho hệ thống xử lý tiền lương, bao gồm các bước chạy bảng lương vào các ngày định kỳ.
    - Employee: Đại diện cho thông tin của nhân viên, bao gồm dữ liệu cần thiết để tính lương.
    - Timecard: Lưu thông tin về thời gian làm việc của nhân viên hưởng lương theo giờ.
    - PurchaseOrder: Lưu trữ các đơn hàng cho nhân viên hưởng hoa hồng để tính phần hoa hồng.
    - BankSystem: Đại diện cho hệ thống ngân hàng xử lý các giao dịch thanh toán.
  b. Mô tả hành vi thông qua biểu đồ tuần tự (sequence diagram):
    - Dưới đây là các biểu đồ sequence mô tả hành vi của hệ thống trong quá trình Run Payroll.
        ![SequenceDiagram](https://planttext.com/api/plantuml/png/V9F1Ri8m38RlF8MFss4lm64IKAHTq2fWsjbBZHerJP2JeFNPTjWZxHMMP6iej91B8yV-Vlzn-lFrNMB7HgbTPnsryFGCw_QeJ4SqXoqvbdIY78827SvGkNDa_IcjipC8AyS2v88wXvBDILRKX_yuiMQalfSj2UHgeDw7u44Ue3QULGVqh_MOA3bZh1medZNiZKC5Bw7OmhlXXgff-TApgD7IArV4WnxwEAG3creHfcsbjT9egguQki3SxcgL2R1eZTTkkgdpH5QeX5Veqascv3YCi6z9EzYGgqq5qi86fGB3K4hH-6DAdBRBKhjeD6tYkQX9DAc0bAK9T26PX8E2ZiPATnkzHDtqTdUagwj2s3DgYy85ynaIpPphejhY59pWXwAS4zSWPtot0p3il11axS6hN9zi3G1l6YSrxXgAxwA3CB1mpUCMWzjP_qro-S_OO7nwS0YZAKXHDdzdv2blWDYIC1ouWVqB003__mC0)
  c. Nhiệm vụ của từng lớp phân tích:
    - PayrollSystem:
          + Khởi động quy trình chạy bảng lương vào các ngày được chỉ định.
          + Kiểm tra tình trạng của hệ thống ngân hàng để gửi giao dịch.
    - Employee:
          + Lưu trữ thông tin cá nhân và thông tin cần thiết cho tính lương.
          + Chuyển các yêu cầu về thanh toán đến lớp thích hợp.
    - Timecard:
          + Ghi lại thời gian làm việc và tính tổng giờ cho nhân viên làm việc theo giờ.
    - PurchaseOrder:
          + Xử lý và lưu thông tin về đơn đặt hàng của nhân viên hoa hồng.
    - BankSystem:
          + Nhận yêu cầu giao dịch từ hệ thống bảng lương và xử lý các thanh toán trực tiếp qua tài khoản ngân hàng.
  d. Một số thuộc tính và quan hệ giữa các lớp:
    - Các thuộc tính:
          + PayrollSystem:
                payrollDate: Ngày chạy bảng lương hiện tại
          + Employee:
                employeeId: ID của nhân viên
                name: Tên của nhân viên
                salary: Lương cơ bản (cho nhân viên hưởng lương tháng)
                benefits: Các khoản phụ cấp và quyền lợi
                deductions: Các khoản khấu trừ
                payMethod: Phương thức thanh toán (gửi ngân hàng, thư, nhận trực tiếp)
          + Timecard:
                employeeId: ID của nhân viên
                hoursWorked: Số giờ làm việc
                date: Ngày làm việc
          + PurchaseOrder:
                orderId: ID của đơn hàng
                employeeId: ID của nhân viên hoa hồng
                commissionRate: Tỷ lệ hoa hồng  
    - Quan hệ giữa các lớp:
          + PayrollSystem là lớp quản lý toàn bộ quy trình xử lý bảng lương, tương tác với các lớp Employee, Timecard, PurchaseOrder và BankSystem.
          + Employee lưu thông tin chi tiết về nhân viên cần thiết cho tính toán tiền lương và xác định phương thức thanh toán.
          + Timecard và PurchaseOrder cung cấp dữ liệu bổ sung cho các nhân viên theo giờ và nhân viên hoa hồng.
          + BankSystem xử lý các giao dịch khi có yêu cầu thanh toán trực tiếp.
  e. Biểu đồ mô tả lớp phân tích:
    - Dưới đây là biểu đồ lớp của ca sử dụng Run Payroll.
      ![ClassDiagram](https://planttext.com/api/plantuml/png/Z5DBQiCm4Dtx55gw2ryWb13wWHPQ6Xf3rnDfcfZe4pHIm9IUh8iUgLUe5CkExIHWRspFcwTvypJpz_Ex80VMUIKpBe68BQ6sHifLJGuL-yfOU0gsRw8Fu93DM7mT0SQirucHtmJaO2gH40wIUnao0vwZsajJOoG_fi-OBenVo_OeGYrASmTwbpiBce2xokYG5KFbATBL-SwIvlR8JcvRxbc4t9MpbTuaH8F2SOn0Wgs7SWgsHesVbQCGVwd8tJQKUK852dzKSmKFXhsYsvgH0COsw9QTcJ0sJQ14X_bvYsMba8CL4rhS6c_fmzWTYd5Fukp-WfpIE91FaPHVEBHtJPsOfRTy2uHlLg3j59duToxdkb1kbAg8WedlZQx1E0Hbzrt2L6LnL0QZozZU6ev4lG6QFbx3PIYA-MdKPinYa847f7OxehrmWTFTNP_Zsk0Lqj3ZGRM4D8RJ1MxFXTbnhKAvKuEKBK8eRlm_0000__y30000)
**II. Viết code Java mô phỏng ca sử dụng Maintain Timecard.**
- Dưới đây là chương trình java mô phỏng ca sử dụng Maintain Timecard:
package Main;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;

class Employee {
    private int employeeId;
    private String name;
    private String email;
    private List<Timecard> timecards = new ArrayList<>();

    public Employee(int employeeId, String name, String email) {
        this.employeeId = employeeId;
        this.name = name;
        this.email = email;
    }

    public void enterHours(Timecard timecard) {
        timecards.add(timecard);
    }

    public void submitTimecard(TimecardManager manager) {
        for (Timecard timecard : timecards) {
            manager.createTimecard(timecard);
        }
    }
}

class Timecard {
    private Date startDate;
    private Date endDate;
    int hoursWorked;

    public Timecard(Date startDate, Date endDate, int hoursWorked) {
        this.startDate = startDate;
        this.endDate = endDate;
        this.hoursWorked = hoursWorked;
    }

    public void updateHours(int hours) {
        this.hoursWorked = hours;
    }

    public void save() {
        System.out.println("Timecard saved!");
    }
}

class Project {
    private int projectId;
    private String projectName;

    public Project(int projectId, String projectName) {
        this.projectId = projectId;
        this.projectName = projectName;
    }

    public List<Project> getProjects() {
        return new ArrayList<>(); 
    }
}

class Validation {
    private int maxHoursPerDay;
    private int maxTotalHours;

    public Validation(int maxHoursPerDay, int maxTotalHours) {
        this.maxHoursPerDay = maxHoursPerDay;
        this.maxTotalHours = maxTotalHours;
    }

    public boolean validateHours(int hours) {
        return hours <= maxTotalHours;
    }
}

class TimecardManager {
    private List<Timecard> timecardList = new ArrayList<>();
    private Validation validation = new Validation(8, 40);

    public Timecard createTimecard(Timecard timecard) {
        if (validateTimecard(timecard)) {
            timecardList.add(timecard);
            timecard.save();
            return timecard;
        } else {
            System.out.println("Timecard không hợp lệ!");
            return null;
        }
    }

    public boolean validateTimecard(Timecard timecard) {
        return validation.validateHours(timecard.hoursWorked);
    }
}

public class MaintainTimecard {
    public static void main(String[] args) {
        Employee employee = new Employee(1, "DinhLuu", "dinhluu@gmail.com");
        Project project = new Project(1, "Project Alpha");

        Timecard timecard = new Timecard(new Date(), new Date(), 35);
        employee.enterHours(timecard);

        TimecardManager manager = new TimecardManager();
        employee.submitTimecard(manager);
    }
}

