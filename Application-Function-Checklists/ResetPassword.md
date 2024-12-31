# Reset Password Vulnerability Checklist

## **Objective**
To identify and test potential vulnerabilities in the password reset functionality that could be exploited by attackers.

## **Key Steps**

### 1. Change Victim’s Email in the Link or Request  
Change the email in the password reset  request, and if that fails, attempt to manipulate parameters such as the one responsible for email verification. By removing or altering parameters, it might allow successful email change, enabling a password change and account takeover.

### 2. Password Reset Link Does Not Expire
If the password reset link does not expire or can be used multiple times to reset the password, it is considered a vulnerability.

### 3. Using Old Password Reset Link
Test if old password reset links still work after new ones have been issued. If an old link is still functional for resetting the password, it is a vulnerability.

### 4. Manipulating the Reset Token
Request a reset token, change the password or email, and then try using the old token to reset the password again. This can result in an account takeover or other security issues.

### 5. Leakage of Reset Token via Referer Headers
After sending the password reset token to the reset page, use tools like Burp Suite to check if the token leaks in the Referer headers or in the response.

### 6. Inserting Attacker's Email with Victim’s in the Request
Try different email formats such as:
- `email=victim@xyz.tld,hacker@xyz.tld`
- `email=victim@xyz.tld%0a%0dcc:hacker@xyz.tld`
- JSON format: `"email": "victim@xyz", "email": "hacker@xyz"`

### 7. Host Header Injection
Intercept the request and modify the host header to `attacker.com`. Check your email to see if the password reset link contains the attacker’s domain.

### 8. Response Manipulation
Change the response text to insert an incorrect OTP (One-Time Password) and check if it allows access to the reset password page without a valid OTP.

### 9. Adding a "Email" Parameter with an Encrypted Value
Add an encrypted email value to the reset password request to change the password for a different user. You can get the encrypted email value from a login request.

### 10. Receiving OTP for Victim's Password Reset on Phone Instead of Email  
In the password reset request, there is only one parameter, which is the email address. We attempt to guess the parameter for the phone number to which the OTP is sent if a phone number is associated with the account. We then add the victim's email and our own phone number. If the OTP is received on the attacker’s number, we will have successfully executed the account takeover vulnerability.

### 11.  Race Condition 
Execute the race condition by sending two requests for a new password using two different email addresses and check if the same token is sent.

### 12. Modifying One Character in the Token
Change a single character at the beginning or end of the reset token and check if the server still validates it incorrectly.

### 13. Changing HTTP Method for Reset Requests
Change the request method from POST to GET or vice versa, and check if it allows bypassing rate limits or leaking tokens.

### 14. Sending Reset Link Over HTTP Instead of HTTPS
If the password reset link is sent over the non-encrypted `http` protocol, an attacker could intercept the link and steal the reset token. Ensure that the link uses `https`.

### 15.  Accessing Account Directly via Reset Link  
If the password reset link allows direct access to the account without requiring a new password to be set, this enables attackers to access the account using only the link. This can be exploited if the link is leaked anywhere, such as on archive sites. The severity of the vulnerability can be escalated by searching for these leaked links.

### 16.  Manipulating the Email Using Hashes and Spaces  
Test modifying the email parameter using hashes or spaces to check if it reveals information indicating the use of a paid service for sending password reset emails. If a rate limit on reset attempts is detected, this could be considered a vulnerability that may lead to financial costs for the company.

### 17. Sending Password Reset Link in Plain Text Without TLS
If the password reset link is sent in plain text instead of using TLS (Transport Layer Security), it exposes the link to interception by attackers.
