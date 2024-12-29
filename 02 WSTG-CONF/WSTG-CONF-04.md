# WSTG-CONF-04: Review Old Backup and Unreferenced Files for Sensitive Information

## Objective
Ensure that old backup files, unreferenced files, or leftover test files do not expose sensitive information or functionality.

## Checklist

### 1. Identify Backup and Temporary Files
- Search for backup files commonly left behind:
  - `.bak`, `.backup`, `.tmp`, `.old`
  - File duplicates with tilde (e.g., `index.php~`).
- Use tools to enumerate files in directories.

### 2. Look for Unreferenced Files
- Review publicly accessible directories for unlinked files.
- Check for test, debug, or old versions of application files.

### 3. Test Access Control
- Verify whether sensitive files are accessible without authentication.
- Examples:
  - Source code files (e.g., `.php`, `.asp`).
  - Environment files (`.env`).

### 4. Analyze Contents of Exposed Files
- Inspect accessible files for:
  - Hardcoded credentials.
  - API keys or tokens.
  - Database connection strings.
  - Sensitive configurations.

### 5. Review Hidden Directories
- Check for directories or files not meant to be publicly accessible:
  - `.git/`
  - `.svn/`
  - `/backup/`

### 6. Check Web Application Logs
- Look for unprotected log files (e.g., `access.log`, `error.log`).

## Tools
- **Dirb/Gobuster**: For directory and file enumeration.
- **Burp Suite**: For manual testing and crafting specific requests.
- **Nmap**: To scan for open directories and files.
- **Nikto**: For identifying exposed files and directories.

---

Let me know if you'd like to refine this section or proceed to the next!
