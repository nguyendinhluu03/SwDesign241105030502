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
    ![Diagram](https://planttext.com/api/plantuml/png/d98nJiCm68Ltd-BVcahq0XrGKIec1aJX0AxparXrxCfsWX3Y94oiBEnawD2Jv0HS0TjrchR9X2VdvULzp_dzs-mMnb9jgr8GGYOmYmlkLCxbyP4mGOqvYBTAb_16m2sK5lMJGIrfYKaLDtDOMSrbFkqzz-xh5wMpP1itvnucEDk4y6GASwWLpyWxEOMcIbgjX40TqRIoXOlcZ5hq3GRqAnYmNFHQAO5KXWYD6TV8xADQKbEi5NNzXdWV7faT0hh4e7QOSpL7--1G8J3AnyYRlZjNSeMwvWmZeqRDdrzJryqxg33_E9XZ-zPBj9IF17YxV-yBJI3TVp8GVFybOTF-x2pal6s-AR2Wjyt75bYX3bCW_GMOpQul9qCk9-KzesSbut_0-qEn1ShCtyW_0000__y30000)
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
    ![Diagram](https://planttext.com/api/plantuml/png/Z5IzJiCm4Dxp5Dv81rwWGXKYWAZ4JoMGc8_u6WnENDaEAAfu4YPM5dOwCF0aVG9UWOiRkqcR8hB4kSztzzrtT_bPV1qQ2zgMkOpssFboyJfZDoB753G_LJfdyP4g2mww6aIf16Eww3nYz71XPX8gZyG3PyN2eZvJfJQDeRcMt8FEC54SFM3W2LlEBz4MbKGLLYifKREuEM_oQLrPiShG9gNMH2F4dYfzai-agX27p9y6R1Y214V7yRBCYIB1uVDS6Elkb3CETatwMTZx4yfVhKEvpzhvIGdUKwP7MjME9rezO6ele80CSs9-31Rkm22BnxMQKqXn40b__CjXlbNA7L8dKYt8MS2GNLijYcoxkXQV3i1YgaZOC0TTS9KkrKYgD5q5xYU1eqHdxkdiPjXW3mNSA0kocIDYEvKAUdk0_z6_LtS_2PjSWdqU2h9Dz7MUJWgYwvt6nouNDQklRCTkL-qhiDajgAwcjuYFpBVCcOioTv84GLev9b1DgCTgIziri8hjDfyc1YbA_MhMbhTDBcxo_POoARxV2_Qu_FooB1FBnGUmrDdhf57djx2_F-hPowXdLTitT-5UqLruTtvtNFfZLORiuA0qE1e5tmujruqk58IC3ack-j_v2m00__y30000)
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
  ![Diagram](https://planttext.com/api/plantuml/png/T591QiCm4Bph5NkB2_K7J0c1KEYXbD0KUXRorXMH9IF9WL3wafvwxQNt-f13Nk8Nz0kL52d4ZgkBbfdLx32htsw_C9PgszQ2p22F1nvR2Ikwqqg84qYOeCOaUAcazJTgU2FWZcvbfB86DLTbuLjNeRo20hQAbw6nGecQMdIi4RmncMVlkR4t4PcJTp8SjaQzvGpZ94O5QyLH8SEw4Mg7MC1jhAx1yXePrSx1KwpyY1UXg0q2ZLOCZV7F9wt-RyOZqKKQ_41hT6_MLdDP7UMJ5fpf1iOgIyMTQhLvLdg3vS1L85t_01o5bPsITAvci3nyCX3yy2LXq__iBLIyxxufi83ttKS3x5MTRvDShY_FvwESoIXstv7IdU9IobDSD4vIU16BeInGbkxh_G400F__0m00)
**4. Bank Interaction Subsystem:**
- Lớp chính:
  + IBankSystem (Interface):
      Phương thức: transferFunds(employeeBankInfo, amount)
  + BankSystem (Implementation):
      Kế thừa IBankSystem
      Hiện thực các phương thức tương tác với API ngân hàng
  + BankInformation (Entity):
      Thuộc tính: bankName, accountNumber, routingNumber
   ![Diagram](https://planttext.com/api/plantuml/png/j5EnQkGm4Etz5TET36j2YgGGOSab9108uI1RNAlLQcsnihH8un0J3W8fKwM-vdBN7HntzRf8iI7_uVn0VY7AxjhnUdrbN1WnysRUUpFII_6mxv1Pp58LV8BJilW-XGEc9-UvGv4UAYaq0ZamcHuncuS1LyovJSHL0FuRYQbn4icKvJmHV4BXo-hKWw4lET5ZOrE6qcYwwD48XC6te4C1a4EZqHgbXDra_mZUWMNQCVwM0tAaKUAQxMPwoSwjO2Z8IiGWdmeAvsYbZdl0KZyvf31MXc4FhCdGny-oT2XiXGeNNLmsJBs5DJcLYxQEEhuK40lylE0X8QoesgOQXhjCDTFBdcjAePBQlQCJZSAE6HT0wcCOo3hQXRngciRtcTBsaAk1oFbl3PDoze0GoxBuou3FxpceDot1ndsCedxpcj3wYeGDR8rgxfHM-zn0rbEdiBUNET7lT_Lg6wNlcsrJ_QUa4rUH1_j2Z_nZVRw-tTwbspjRaVElGyTRKIByCwPzQcX428qI-EfLeNtwvoV4OP98YClYZnmavUmN74ib75pCVnXul9l_pFs_B6xWqfUeSdOlEmfV0G00__y30000)
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
