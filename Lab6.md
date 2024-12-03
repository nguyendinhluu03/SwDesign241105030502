**#4451050894_NguyenDinhLuu**
-------------------------------------------------------------------
**#Dưới đây là thiết kế chi tiết các lớp trong từng hệ thống con dựa vào kết quả thiết kế ca sử dụng ở bài lab trước:**
**1. Authentication Subsystem:**
- Lớp chính:
  + LoginForm (Boundary):
      Thuộc tính: username, password
      Phương thức: submitLogin(), displayErrorMessage()
  + AuthenticationSystem (Control):
      Thuộc tính: userDatabase
      Phương thức: authenticate(username, password), manageSession(user)
  + UserDatabase (Entity):
      Thuộc tính: users (danh sách người dùng)
      Phương thức: findUser(username), validatePassword(user, password)
**2. Timecard Management Subsystem:**
- Lớp chính:
  + TimecardForm (Boundary):
      Thuộc tính: timecardData
      Phương thức: inputTimecard(), displayTimecard()
  + TimecardController (Control):
      Thuộc tính: timecardDatabase
      Phương thức: getTimecard(employeeId), saveTimecard(timecard)
  + Timecard (Entity):
      Thuộc tính: employeeId, date, hoursWorked, projectCode
  + ProjectManagementDatabase (Subsystem):
      Phương thức: getProjectCode(projectName)
**3. Payroll Processing Subsystem:**
- Lớp chính:
  + PayrollController (Control):
      Thuộc tính: employeeData, payrollDatabase
      Phương thức: calculateSalary(employeeId), processPayroll(employeeId)
  + Employee (Entity):
      Thuộc tính: employeeId, name, salaryType, bankDetails
  + Paycheck (Entity):
      Thuộc tính: employeeId, amount, paymentDate, status
  + SystemClockInterface (Boundary):
      Phương thức: getCurrentDateTime()
  + BankSystem (Subsystem):
      Phương thức: processPayment(employee, amount)
**4. Bank Interaction Subsystem:**
- Lớp chính:
  + IBankSystem (Interface):
      Phương thức: transferFunds(employeeBankInfo, amount)
  + BankSystem (Implementation):
      Kế thừa IBankSystem
      Hiện thực các phương thức tương tác với API ngân hàng
  + BankInformation (Entity):
      Thuộc tính: bankName, accountNumber, routingNumber
**5. Printing Subsystem:**
- Lớp chính: 
  + IPrintService (Interface):
      Phương thức: printDocument(documentData)
  + PrintService (Implementation):
      Kế thừa IPrintService
      Hiện thực: printDocument(documentData)
  + Paycheck (Entity):
      Sử dụng từ Payroll Processing Subsystem
**6. Project Management Subsystem:**
- Lớp chính:
  + IProjectManagementDatabase (Interface):
      Phương thức: getProjectCodes()
  + ProjectManagementDatabase (Implementation):
      Kế thừa IProjectManagementDatabase
      Hiện thực: getProjectCodes()
**7. System Clock Subsystem:**
- Lớp chính:
  + SystemClockInterface (Boundary):
      Phương thức: getCurrentTime(), synchronizeTime()
**8. Distribution Subsystem:**
- Lớp chính:
  + IPayrollController (Interface):
      Phương thức: processRemotePayrollRequest(request)
  + NamingService (Subsystem):
      Phương thức: lookupService(serviceName)
