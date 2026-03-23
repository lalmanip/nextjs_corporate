# nextjs_corporate

Corporate Module for Vivance Travels

# Requirements

1. Have a login page with Username and Password. Once Login credentials are entered, call this API - {{baseURL}}/vivapi-user/user/authenticate (POST)
   Sample Request: { "userName" : "myUser", "password" : "mypasswd" }
   Sample Response: { "response": { "userId": 71, "userType": 4, "email": "createuser11@gmail.com", "userName": "myUser", "password": "mypasswd", "status": 0, "firstName": "Create", "middleName": null, "lastName": "User", "countryCode": 92, "phone": null, "emailActivation": false, "createdBy": null, "createdOn": "2025-01-26T21:37:01.000+00:00", "modifiedBy": null, "modifiedOn": "2025-01-26T21:37:01.000+00:00" }, "message": null, "status": "success" }

2. Login page should also have Forget Password link. Once clicked, it should ask for Email and Phone number. Once provided, it should call API - {{baseURL}}/vivapi-user/user/forgotpasswd (POST)
   The response will have new password. Send the new password through the email to the user (to the provided email address)

3. The Login Page should also have "Create Account" link. If "Create Account" link is clicked, the registration form will be opened with following fields -
   a) Personal Info : First Name, Last Name, Mobile Number, Email, Address Proof ,Country, State, City
   b) Company Details : Corporate ID _, Name of Sale's Person _, Company Name _, Pan No, Pan Card Holder Name, Address _, Pin Code _, Office Phone _, Establishment Date,Annual Transaction _, IATA, GST File, PAN File, No of Employees _
   c) Bank Details: Account Number _, IFSC Code _, Account Holder Name _
   d) Login Info : User Name _, Password _, Confirm Password _

Once Register button is clicked, it should call -
{{baseURL}}/vivapi-user/user/create (POST) to create user credentials. The request would be like -

{
"userType" : "7",
"email" : "<From form>",
"userName" : "<From form>",
"password" : "<From form>",
"status" : "0",
"firstName": "<From form>",
"lastName": "<From form>",,
"countryCode" : "92"
}

Once we get response, we call second API -

    {{baseURL}}/vivapi-user/user/corporate/add (POST method)

    {

"userId": <From previous API response>,
"userType": 7, "address": , "addressProof": null, "countryName": , "state": , "city": , "pinCode": , "companyName": , "panNumber": , "panFilePath": null, "gstNumber": , "gstFilePath": null, "officePhone":

}

4. Once logged in, it should have avatar at top right corner with User Name(obtained from response). It should have option to edit profile, Change Password and Sign out

5. Once logged in, It should land on Dashboard which will have flight search facility.

6. Another link is for Reports. Which should allow to -
   a) Booking Details
   b) Executive Booking Details
   c) PNR Search
   d) Pending Ticket
   e) Daily Sales Report
   f) Account Ledger
   g) Transaction Logs
7. Another link is for Payment. Under this link, we have "Update Balance" and "Bank Account Details"
