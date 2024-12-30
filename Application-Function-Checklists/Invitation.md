# **Invitation Vulnerability Checklist**

## **Objective**  
To identify and test potential vulnerabilities in the invitation process that could be exploited by attackers.

### **Key Steps**

### 1. **Invitation of a person to the team, then capturing the request and changing the cookies to those of a non-privileged member.**
   - **Test:** Change the cookies to those of a member who is not authorized to invite someone to the team, and verify if the invitation is still successful. If successful, this would be a privilege escalation vulnerability.

### 2. **Invitation link used as email verification bypass.**
   - **Test:** Check if accepting an invitation automatically verifies the email, bypassing the need for email confirmation.

### 3. **Resending invitation to the same account.**
   - **Test:** Resend an invitation to the same account and check the response. If an invitation link is leaked, it can potentially be used to hijack the account. 

### 4. **Invitation link with no expiration time.**
   - **Test:** Check if invitation links never expire, and test if archived links containing invitation tokens can be used to gain unauthorized access.

### 5. **Blocking new users from logging in even after password reset.**
   - **Test:** Try resetting the password of a newly invited user who has not yet verified their email. Check if the login still fails after resetting, which indicates a flaw in the email verification process.

### 6. **Password reset vulnerability in invitations.**
   - **Test:** Add a new password field (e.g., "password": "example123") in the invitation request. Check if this results in a password reset for the invited user.

### 7. **Role manipulation during invitation acceptance.**
   - **Test:** Attempt to send an invitation with a role parameter and check if the role can be escalated to admin or a higher role.

### 8. **Join team without invitation link.**
   - **Test:** Try to access the team without using the invitation link and verify if access is granted. If successful, this could indicate a vulnerability allowing unauthorized access to the team.

### 9. **Deleting pending invitations as a user with lower privileges.**
   - **Test:** Attempt to delete pending invitations sent by an admin to check if this action is allowed by users without admin rights.

### 10. **Decoding invitation token.**
   - **Test:** If the invitation token is generated using a known algorithm, attempt to decode it. If successful, try to generate new tokens to invite other users.

### 11. **Changing group/organization name in invitation link.**
   - **Test:** Modify the group or organization name in the invitation URL and check if it allows you to join a different group or organization.

### 12. **Invitation link sent over HTTP instead of HTTPS.**
   - **Test:** Check if the invitation link is sent over HTTP instead of HTTPS, which would make it vulnerable to interception on unprotected networks.

###  13 **Automatic acceptance of invitation when logged in.**
- **Test:** If the invited user is not logged in when they receive the invitation, check if clicking on the invitation automatically logs them in and accepts the invitation without asking for confirmation.

### 14. **Email address exposure through invitation.**
- **Test:** When sending an invitation using only a username, check if the email address of the user is exposed in the invitation response or URL.

### 15. **Performing actions in the team without accepting the invitation.**
- **Test:** Check if it’s possible to perform actions in the team without accepting the invitation first.

### 16. **Email domain bypass using special characters.**
- **Test:** If email invitations are blocked for certain domains (e.g., `yopmaįl.com`), try using a character like "į" instead of "I" to bypass the restriction.

### 17. **HTML injection in invitation email.**
- **Test:** Try injecting HTML (e.g., `<a href=evil.com>click</a>`) into the invitation message field to check for potential XSS vulnerabilities.

### 18. **CSRF vulnerability in invitation request.**
- **Test:** Check if a CSRF attack can be performed by modifying the invitation request, potentially granting elevated roles or team control.

### 19. **Invitation token leakage in external requests.**
- **Test:** Check if invitation tokens are exposed in external service requests, such as Google Analytics, which could lead to leakage or misuse of tokens.

### 20. **Race condition in team invitations.**
- **Test:** Test for race conditions by sending multiple invitations or accepting them simultaneously to see if it allows exceeding the invitation limit or allows an attacker to bypass restrictions.

### 21. **Lack of invitation cancellation option.**
- **Test:** Check if invitations sent to users without accounts can be canceled, and verify if a user can rejoin the team by creating an account with the same email after being removed.

### 22. **Rejoining team via invitation link after revoking the invitation.**
- **Test:** If the invitation link is revoked, check if an attacker can still use the link to join the team after receiving a reminder email.

### 23. **Invitation link showing as a malicious URL.**
- **Test:** Create a team name with a malicious URL (e.g., `https://attacker.com`) and send the invitation. Check if the URL is displayed as part of the invitation email.

### 24. **Name or email change vulnerability in invitation response.**
- **Test:** Attempt to change the name in the invitation to a malicious URL, which could allow the attacker to send a phishing link within the invitation email.

### 25. **Exploiting race conditions in invitation requests.**
- **Test:** Test if the race condition occurs by sending duplicate invitations to the same user, which could result in errors, inability to delete, or Dos.

### 26. **Invitation link exposure via HTTP.**
- **Test:** Check if the invitation link is sent over HTTP instead of HTTPS. This can allow attackers in the same network to intercept and steal the invitation token or even hijack the account.

### 27. **Requesting invitation actions with expired session.**
- **Test:** Try sending invitation requests using an expired session, such as after logging out or changing the email/password, to see if actions still go through.

### 28. **Invitation field with no character limit.**
- **Test:** Check if the invitation form allows an excessively long name (e.g., 200 characters) in the name field, which could be used for phishing or social engineering attacks.

### 29. **No rate limit on invitation requests.**
- **Test:** Check if the invitation form has a rate limit. If not, attempt to spam the form with multiple random or repeated requests to flood the system.

### 30. **Invitation link guessability.**
- **Test:** If the invitation link consists of simple numbers or short strings, try guessing the link and see if you can gain unauthorized access to the victim's account or obtain sensitive data.
