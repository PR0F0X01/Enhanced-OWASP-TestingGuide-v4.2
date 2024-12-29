# WSTG-INFO-01: Conduct Search Engine Discovery and Reconnaissance for Information Leakage

## Objective
To identify sensitive or unintended information available publicly via search engines and other online platforms that could be exploited by attackers.

## Key Steps

### 1. Perform Basic Search Queries
Use search engines like Google, Bing, or DuckDuckGo to gather general information about the target organization.
- Examples of queries:
  - `site:targetdomain.com`
  - `inurl:admin site:targetdomain.com`
  - `filetype:pdf site:targetdomain.com`

### 2. Search for Sensitive Files
Identify sensitive files or directories exposed to the public.
- Common extensions to look for:
  - `.pdf`, `.docx`, `.xlsx`
  - `.bak`, `.sql`
  - `.env`, `.config`

### 3. Leverage Search Engine Operators
Use advanced operators to refine searches:
- `intitle:` to search for specific text in page titles.
- `inurl:` to locate specific text in URLs.
- `cache:` to view cached versions of pages.

### 4. Check for Indexed Internal Pages
Identify internal or staging pages inadvertently indexed by search engines.
- Examples:
  - `site:targetdomain.com inurl:test`
  - `site:targetdomain.com inurl:staging`

### 5. Look for Exposed Credentials or Code
Search for possible credentials or code snippets accidentally published online:
- Queries:
  - `password site:github.com targetdomain`
  - `site:pastebin.com targetdomain`
  - `site:targetdomain.com API key`

### 6. Review Third-Party Sources
Search for information about the target organization on third-party websites.
- Sources:
  - Pastebin
  - GitHub repositories
  - Public forums

### 7. Use Automated Tools
Utilize tools to automate and enhance reconnaissance:
- [GoogDork](https://github.com/ZephrFish/GoogDork)
- [Photon](https://github.com/s0md3v/Photon)
- [Recon-ng](https://github.com/lanmaster53/recon-ng)

### 8. Document Findings
Maintain detailed notes on discovered sensitive data:
- URLs of sensitive pages/files
- Description of the data found
- Potential impact of information leakage

## Tools and Resources
- **Search Engines**: Google, Bing, DuckDuckGo
- **Tools**:
  - Recon-ng
  - Photon
  - GoogDork
- **Websites**:
  - [Exploit-DB Google Hacking Database](https://www.exploit-db.com/google-hacking-database)

## Mitigation Recommendations
- Use `robots.txt` to restrict indexing of sensitive directories or files.
- Implement access controls to secure sensitive content.
- Regularly review search engine indexes for unintended exposure.

---

**Next Steps:**
Proceed to [WSTG-INFO-02: Fingerprint Web Server](./WSTG_INFO_02.md).
