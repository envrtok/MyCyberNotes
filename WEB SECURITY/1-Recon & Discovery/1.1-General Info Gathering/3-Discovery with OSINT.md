Reconnaissance is about building a map of the target's attack surface without ever sending a packet directly to their servers (Passive Recon).

### 1. Advanced Search (Google Dorking)

- **Subdomain Discovery:** `site:*.target.com -www`
    
- **Sensitive Files:** `site:target.com filetype:env OR filetype:conf`
    
- **Login Pages:** `site:target.com inurl:login | admin`
    

### 2. Entity Harvesting (theHarvester) 🆕

Before you touch the website, use this to scrape the entire internet for clues about the organization's infrastructure and people.

- **What it finds:** Emails, names, subdomains, IP addresses, and open ports via Shodan.
    
- **The Goal:** Build a target list for social engineering (phishing) or identify "forgotten" subdomains that search engines missed.
    
- **Quick Command:** > `theHarvester -d target.com -l 500 -b google,bing,linkedin,shodan`
    
    > _(Searches 500 results across Google, Bing, LinkedIn, and Shodan)_
    

### 3. Tech Stack Profiling (Wappalyzer)

- **What to look for:** CMS (WordPress), Web Server (Nginx), and JavaScript Frameworks.
    
- **Strategy:** Identify version numbers. Outdated frameworks (like **jQuery 1.12**) are instant red flags.
    

### 4. Historical Data (Web Archive)

- **The Goal:** Find old endpoints or deleted "coming soon" pages that might still be active on the server.
    
- **Pro Tip:** Look for old `/robots.txt` files; they often list directories the company _used_ to want hidden.
    

### 5. Code Leakage (GitHub)

- **Search for:** `target.com "API_KEY"` or `target.com "password"`.
    
- **Check History:** Look at the **Commit History**. Developers often "delete" a secret in a new commit, but it stays in the git logs forever.
    

### 6. Cloud Infrastructure (S3 Buckets)

- **Common Naming:** `target-stage`, `target-backup`, `target-assets`.
    
- **Testing:** Use tools like **S3Scanner** to see if permissions are accidentally set to "Public."
    

---

### 🔍 Updated Summary Table

| **Tool**            | **Primary Purpose** | **Best For...**                                    |
| ------------------- | ------------------- | -------------------------------------------------- |
| **Google Dorks**    | Search Hacking      | Finding indexed sensitive files/configs.           |
| **theHarvester**    | Mass Gathering      | Collecting emails and subdomains from 20+ sources. |
| **Wappalyzer**      | Fingerprinting      | Identifying the tech stack and CVE-prone versions. |
| **Wayback Machine** | Historical Recon    | Finding old endpoints or "hidden" directories.     |
| **GitHub**          | Secret Hunting      | Finding leaked API keys and hardcoded credentials. |
| **S3 Buckets**      | Cloud Discovery     | Locating exposed databases or private assets.      |
