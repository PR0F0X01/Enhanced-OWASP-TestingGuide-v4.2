# **Email Verification Vulnerability Checklist**

## Objective:
To identify and test potential vulnerabilities in the email verification process that attackers could exploit.

## **Key Steps**

### **1. Bypass Email Verification via Login and Email Change**  
- Change the email address in the account to one you control.  
- Use the confirmation link sent to your email, but modify the address to the victim's email before confirmation. Then, confirm the victim's email.

### **2. Multiple Accounts with a Single Email**  
- Create multiple accounts with the same unverified email.  
- When the victim registers and confirms their account, all associated accounts are automatically verified.

### **3. Modify Parameters in Login or Action Requests**  
- Inspect requests or responses during actions (e.g., login or password change).  
- If there's a parameter like `email_verified`, switch its value from `false` to `true` (or `0` to `1`).
- Bypass verification by manipulating cookies, response codes, or values such as `false` to `true`.

### **4. Parameter Disclosure in Request for Confirmation Links**  
- Add the confirmation parameter when requesting an email verification link.  
- Check if the confirmation token is leaked in the response.

### **5. Host Header Injection in Verification Link**  
- Inject your own host into the email confirmation link.  
- When the victim clicks it, the request is logged on your controlled host, allowing you to capture sensitive information.

### **6. Brute Force Headers or Parameters**  
- Attempt brute force attacks on headers or parameters in requests to discover confirmation tokens or manipulate confirmation messages.

### **7. Archiving Confirmation Links**  
- Search web archives (e.g., Wayback Machine) for exposed confirmation links.  
- If links are functional post-confirmation, they can be exploited to access accounts.

### **8. Using Unverified Email for Site Functions**  
- Test if site features (e.g., posting, commenting) work with unverified emails.  

### **9. Analyze Confirmation Tokens**  
- Send multiple confirmation requests from different accounts.  
- Check for predictable patterns in token values or decode them to uncover weaknesses.

### **10. Personal Data Leaks**  
- Check if sensitive data like `auth tokens`, `user_id`, or the email address leaks in responses.  

### **11. Exploit Email Change Confirmation Links**  
- If a confirmation link for email changes is sent to the new email, check if opening it while logged into the account changes the email automatically.  
- This can lead to account takeover.

### **12. Email Change Exploit via Request Parameter**  
- If the target does not allow direct email changes but permits name changes, intercept the request when updating the name. Look for an email parameter in the request or try guessing it.  
- If you can modify the email to that of an existing victim (e.g., admin or other important account), report this as a **zero-click account takeover** vulnerability.


### **13. Race Condition in Simultaneous Confirmation and Change Requests**  
- Exploit a race condition by triggering both confirmation and email change requests simultaneously.  
- If the system processes both requests without proper validation, it might confirm the victim’s email for your account, resulting in an account takeover.

### **14. Email Auto-Confirmation via Team Invitation**  
- Create an account without confirming the email.  
- Invite this unconfirmed account to a team from another account.  
- If the invitation acceptance automatically confirms the email without requiring manual verification via the confirmation link, it bypasses the email verification process entirely.

### **15. Exploit CSRF in Email Updates**  
- Test for CSRF vulnerabilities in endpoints like email updates.  
- If the CSRF protection is bypassable, manipulate the requests to gain access.

### **16. Email Confirmation Link Used for Account Takeover**  
- If the email confirmation link grants direct access to the account without requesting a password or additional authentication, the attacker can send this link to the victim.  
- When the victim clicks the link, they are logged in, believing it is their account. Meanwhile, the attacker gains access to all activities and sensitive information associated with the account.

### **17. OAuth Linking for Email Verification Bypass**  
- Link an unverified email to an OAuth provider (e.g., Google).  
- Once verified through OAuth, unlink the provider, bypassing email verification.

### **18. Reuse of Tokens Post-Verification**  
- Check if email verification tokens work after the email is confirmed.  
- If functional, try using them for unauthorized access or password reset.

### **19. Adding Emails Without Verification**  
- Create an account, verify it, and later add an unverified email (e.g., victim’s).  
- The email might be added without re-verification, bypassing security.

### **20. Access APIs with Unverified Emails**  
- After changing the email to an unverified one, check if sensitive functions like API access still work.  
- Exploit this to gain access to sensitive data or functions.

### **21. Confirm Email Changes Fully**  
- Verify email change processes to ensure login attempts with the old email fail.  
- If not enforced, old email credentials might still work.
