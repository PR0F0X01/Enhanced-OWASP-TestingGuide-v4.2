# OAuth Vulnerability Checklist

## **Objective**
To identify and test potential vulnerabilities in the OAuth authentication and authorization process that could be exploited by attackers.

## **Key Steps**

### **1. Exploiting Open Redirect in OAuth**  
- The attacker exploited the `open_redirect` parameter by replacing the legitimate domain with the attacker's domain. After sending the login link using OAuth to the victim, and after the user logs in and selects an account (e.g., Google account), the user is redirected to the attacker’s site to steal the authorization code.

### **2. Open Redirect via `redirect_uri` Parameter Using Cyrillic Characters**
- The attacker uses Cyrillic characters in the domain, such as `tārġet.com`, making the server believe it's a legitimate domain similar to the original domain.

### **3. Using Traversal Path in `redirect_uri`**
- The attacker sends a link with a modified `redirect_uri` using traversal path to point to the attacker's product page, such as:  
  `redirect_uri=https://target.com/../../redirect_url=https://www.evilsite.com/a.php%2Fcomplete`.

### **4. Exploiting Subdomains to Bypass `redirect_uri`**  
If the `redirect_uri` parameter accepts any subdomain of the site, the attacker searches for open redirect vulnerabilities in the site's subdomains. By exploiting this, they can add a malicious subdomain link. This allows the attacker to redirect the victim to their own site instead of the legitimate one.

### **5. Exploiting `redirect_uri` Parameter to Bypass Path Traversal**

- The attacker manipulates the `redirect_uri` parameter to redirect the victim to a specific product page, for example:
`redirect_uri=https%3A%2F%2Ftarget.com%2Fusers%2Fauth%2Fcallback/../../../../product/12345`
- The result is: `https://target.com/product/12345`
- This redirects the victim to the attacker's product page. If Google Analytics is enabled, the query string may expose the authorization code, potentially leading to a leak of the unused code.

### **6. Exploiting Disabling Email Sharing Option**  
- During the OAuth login process, the attacker disables the email sharing option, which causes a prompt to manually enter an email address. The attacker then enters the victim's email address instead of their own, leading to account takeover after login.

- ### **7. Pre-registering and Confirming via Google**
- The attacker registers an account using the victim’s email address beforehand. When the victim tries to sign up via Google with the same email, the account is linked to the attacker, allowing account takeover.

### **8. Testing Access Token Expiry After Disconnecting Third-party Account**
- Test if the access token can still be used after disconnecting a third-party account (e.g., Google). Generate multiple tokens and check if revoked tokens are still valid or accessible.

### **9. Leaking OAuth Tokens in Referer Header**
- Check if OAuth tokens are leaked in the `Referer` header during navigation between different domains .

### **10. Token Reuse**
- Check if OAuth tokens can be reused across multiple sessions, for different users, or if expired tokens are still accepted.

### **11. Missing or Disabled `state` Parameter**
- Ensure the `state` parameter is present and correctly validated to prevent CSRF attacks. Test CSRF bypass techniques or send the code without it to link the victim's account to the attacker's email.

### **12. Exploiting Exposed Client_secret**  
- The attacker uses tools like **Burp Suite** or techniques like **GitHub Dorking** to search for exposed **API keys** or **Client_secret** used in OAuth.  

### **13. Lack of Access Token Validation**
- Test if the site validates the access token properly, ensuring that it only accepts valid tokens from authorized sources. Without proper validation, an attacker could bypass authentication.

### **14. Exploiting OAuth Server Vulnerabilities**  
- If the target allows using its site as an OAuth provider for other websites, the attacker can create a malicious application that requests limited permissions, such as email (`openid email`). After the user consents, the attacker modifies the request to add additional permissions (e.g., `profile`).  
- If the OAuth server does not properly validate the permissions, it issues an access token with extended permissions, potentially giving the attacker full access to the user's data. 

### **15. Unconfirmed Email Accounts Used for OAuth Login**  
- If the target allows using its site as an OAuth provider for other websites, the attacker creates an account without confirming the email and tests if it can be used to sign in via OAuth. This tests the system's handling of unconfirmed accounts during the OAuth login process. If the OAuth server does not properly validate the email confirmation, the attacker may be able to use an unconfirmed account for unauthorized access.

### **16. Granting Access at the Start of OAuth Instead of the End**
- Check if the system grants access to the user at the start of the OAuth process, skipping third-party authentication entirely.

### **17. Linking Victim's Unconfirmed Email to OAuth Account**
- The attacker links the victim’s unconfirmed email to their OAuth account, blocking the victim from registering or logging in with that email.

### **18. Replacing Email in OAuth Link for Account Takeover**
- When linking an OAuth account (e.g., Google), replace the email with the victim’s email address to link the victim’s account to the attacker’s account, resulting in account takeover.

- ### **19. Exploiting Google Login for Account Takeover**  
- After logging in via Google, the attacker modifies the session details (email, username, or ID) to match the victim's, gaining access to their account if the system doesn't properly validate the token.

### **20. OAuth2 Endpoint Manipulation**  
- The attacker adds `.json` or `.xml` to the OAuth2 endpoint URL (e.g., `POST /authorization.json`) to receive an unauthorized authorization code, bypassing restrictions.

### **21. Google Account Takeover Persistence**  
- After the victim changes their email and disconnects the previous authentication (e.g., Google), the attacker may still be able to log in using Google login if the system doesn’t properly disconnect or revalidate the session, leaving the attacker with persistent access.
