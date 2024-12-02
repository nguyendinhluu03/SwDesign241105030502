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
- Biểu đồ: ![Authentication Subsystem](https://planttext.com/api/plantuml/png/V98zJiCm5CVtdE8f4mmLUmPKH0L8L5rI3k0uKMAriOlpWeWG4mChFG0I5UfO2IGMag538kxX4t05R2zrK67pa_yVlsVvkzaE2oGIotpkBGYTaJG1_wJ4BE78A44cE8HbL5G59haFTnu0eIWaN1M915A0Fqc_tbJpp21kFtdgQq4aIXuJMS5Of8oV2PbRePt0Z4P41KSfvj3l2csFbL-evX4mKysIft3RhgWTtgan6mDMbc54a4IaIApdD1oDuJUGrblOmU1uHnJ095FrPg53smzTW1gjMtOF-iZjXNRjy8rr7sW0vwhPC2T4s_PkP19St02cigpWHjLhthVtblgx-5BLMuJhKjMlxklyr-yiFvN6DtCo3hedPtk3zC8pe0RiI4VNQuH8rIjswDrxmuJ7viFy0000__y30000)
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
- Biểu đồ:
  ![Timecard Management Subsystem](https://planttext.com/api/plantuml/png/Z9CnIyD068Rt_8gFxALx1ocqQWSjYWvrl5oE9ZPtLvCx8OY3E3Yuw4-eHOI2gE2K31qY_e_y0l-2toMqISMWKyXnx_Ezx_ibN-co6oaIAiq3QqheX8mPsCS-PvI4BkmJWGUS2GL7sedYI35kmuK5GAYI8MppQI1Zne14O0-zx470kPyjX8qt7Ac5Iy8OLhGT6VBYugvF9BX-dju8SF9aBiP0lJnvv42pTp4sOYg52cMmrlRAzu251U7Z3jLN6YOUFgyRAUZRLvM1GjhFqnS8p73zX-mWbAUCggg3Fb748L6PTe04K5wUtYFXS0-G-mRP3ACZOTrBgxMraRy38yRRGnpuF4MrcGZA5oZPQAakgw9tu2HRQA1vygJ1hNBKrBMU3ACnGWVsC7CCF9iRKk4SCSsHcnprYV0WocRK-ybgiBGwHWUVhxhTAveGfX3rspvge4OF8nnV8lunjzp2eFnkpFvkOP8dImLd6gTRbrQN2TVy3Ty0003__mC0)
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
- Biểu đồ:
  ![Payroll Processing Subsystem](https://planttext.com/api/plantuml/png/X9CzIiH05CVxFSKZ_LuWXOYhI50ai7k1oMJC34bcbiba8OY5MDWALXQ2gzZOg62L55j4zXvp0g_Wv8lDkWQh4FX_lFTxoNUnsayKaYgDez4SuH0512mNPL944RXIO98aZ0SmJRqaInI9BRWO0M31bP50gvmqhn6HW1AmlcwPBgvI2AbvNdFmTFviCgBr-th90yluFP5o7yaCfdNe918uTBWYyXnXqcReuiwOF5tSWwAwU60GCCIttCu1uc4JKPkE6HBWcz8R3ZmedpZGyl5Ne-DAnjMKo0Lhg_ekLXSGhfZAu2YUHo8ZZUgCLdaBLhxs9JCM4uoaNqiETV46KHMKTZjZglEN673vsOpHsWmtJ0aEQvjhCEMhTCF7w7R1ZiTxVzAouQIY78EIg0zgCAGRsOPJCri6Vc_g_hY30HsMBa3HIWwA6UWRI8FsRdSRPZfV2fXlhp_ewntRMCsY7nXeSpLCqwp-qlxDw1_V1eVlj5-EzWdtgz_X1m00__y30000)
**4. Bank Interaction Subsystem (Tương tác ngân hàng):**
- Mô tả: Tích hợp với các hệ thống ngân hàng để thực hiện giao dịch.
- Thành phần chính:
    + IBankSystem (interface): Định nghĩa giao diện giao tiếp ngân hàng.
    + BankSystem (subsystem): Hiện thực giao tiếp với ngân hàng.
    + BankInformation, Paycheck (entities): Dữ liệu cần thiết cho giao dịch.
- Chức năng chính:
    + Thực hiện chuyển khoản lương.
    + Kiểm tra trạng thái giao dịch.
- Biểu đồ: ![Bank Interaction Subsystem](https://planttext.com/api/plantuml/png/V98zJiCm5CVtdEAlxBr01rJ1K2gMIkq5NDUDhQGlaDX3X1WG0mCBt82F0Ga92IIcPkWGr7la15o1vnIaD1LCjgNt-tyy-QjS3t8hCkkMIN0gP2mYXV1GK8mHMPK9QKrAcBXPNkHMBKES1u1CoMPfWh4e-4YEjiz4PH0vmizRKvUN3h7cyuemgrTF527Pl6qUA0gPDrvw8QJ2o5jD6kc67HgHOixSDO6Ywf6Wg_ijz6lQ8Ovv5bRNvHrxT115rjZ2nvHQoRYP7tEgrTgru_oCUU4HBT9iAPhIVdgggm_MjQOJXwdzyhtUGRjG7yEwV3KegXS7MQ-U7QAcNbtUICqAxVAURQDJRlGkeRUhsEKws8xbDEDj8-QA5cVEt__tt6lHnyaVy4KmK3Jt7-KR003__mC0)
**5. Printing Subsystem (In phiếu lương):**
- Mô tả: Quản lý in ấn cho phiếu lương nhân viên 
- Thành phần chính:
    + IPrintService (interface): Giao diện chuẩn hóa cho dịch vụ in.
    + PrintService (subsystem): Hiện thực logic in phiếu lương.
    + Paycheck (entity): Dữ liệu phiếu lương.
- Chức năng chính:
    + In hoặc xuất phiếu lương dưới dạng tệp.
    + Quản lý trạng thái và kết quả in.
- Biểu đồ: ![Printing Subsystem](https://planttext.com/api/plantuml/png/R94nIWD168NxdEAnVIwGGW8AGMmMOcCvcHrtXvtC9hCpWKKinCB2nYi44K4GhNUA597SOqxW5Vmd4NHNgvyVtlVU-sS-_MPSMsQicwl1Wl6IvG99QgIsKkUOkbdTr5RC4rmD05vfQog5b3KqrF5XLSA0rKW-7cJmDmvbGVDMOnRQH_9Gk_VTMkS9yUGgp2NZ0gVxYAamAqbRf2UILSY8lDEaItwdzQKdmT_p0glWdxwbWkhQ9lRYXU3bNfLIZNRZVl99zxVuS7ZKBJF2nVR5WOVssP4x5bqRCkbsZmPTVXBygqGM_1jKl2VQnEm-rOizDw6b0DXYkvO7v9-a_W4Zd54zYwMZruxKzM0iT1Q_ymi00F__0m00)
**6. Project Management Subsystem (Quản lý dự án):**
- Mô tả: Cung cấp mã dự án cho các hoạt động chấm công.
- Thành phần chính:
    + IProjectManagementDatabase (interface): Giao diện với hệ thống quản lý dự án.
    + ProjectManagementDatabase (subsystem): Hiện thực việc lấy dữ liệu dự án.
- Chức năng chính:
    + Lấy danh sách mã dự án từ cơ sở dự liệu.
    + Tích hợp với hệ thống quản lý dự án kế thừa.
- Biểu đồ: ![Project Management Subsystem](https://planttext.com/api/plantuml/png/XD8nIiH050RWFgVuIRyNs48MN511GJ6DvSjaJE9cNcGo8onY8HQsUeHb4S561Akai8WNcHDu1ISgheioLiChvfl_VynRzp9f36bZLHMTafXHBX7lw_f42eCzOZyhoGQ7DctcZP4gnda4Y9gDhYiafPA2TBRvELTIWnh4hpUbwoujPeK_hnYfQvUSGnIklLCG_JFdiLTADb8Vav3O-NfozUAK3ANKo0zlgwGQcRUk6GUxo5ptX7x1yOyaOM3RNuKfN7VhOwm9dlYZn6Yq4SWqnb7_O25SUs-X-kKtvx50am4Dc8csSvpv3V7WFQ8Q-bfFXiLGp4JxnICZBj3q2r4COV_F-7iVOqpNZ5NXYsWYEHj-ppi0003__mC0)
**7. System Clock Subsystem (Đồng bộ thời gian hệ thống):**
- Mô tả: Quản lý và chuẩn hóa việc sử dụng thời gian trong hệ thống.
- Thành phần chính:
    + SystemClockInterface (boundary): Lấy thời gian từ hệ thống.
- Chức năng chính:
    + Đồng bộ thời gian trong các tác vụ (trả lương, nộp bảng chấm công).
    + Giảm sai lệnh thời gian giữa các thành phần.
- Biểu đồ: ![System Clock Subsystem](https://planttext.com/api/plantuml/png/fD8nIiH050RWFgVucNuli8KiR2LO2BiNc4p6ISZaHIQJ8eZ5ieMjOcLXiOYzXLMci53s7dC2h-0aiGWaB8BLunN_D_-3-NOVgyfoO-j2HzTSv5n9i4rJMLbWhKkHOrF7LRypt4I0ACcQKkEIDs7ezR1gQS0hiA_xpBjTZJmDSq-8VVj22lhuTZoGOgFyDYkau2Rv6o1ItxuM49_lWnANDINSD1YgzatFoKfpnONyXRnx3CdOkoVOrBld32hZnA8GdvPVBCvchIKkmilDM41NxOvWVNl80ZPpoJ-qsOCwRz9vYUsO2KhlFf0wnKpRdd1kevMafFiRFm000F__0m00)
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


