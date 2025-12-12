HTTP Security Headers strengthen web applications by mitigating attacks like **XSS**, **clickjacking**, and more.  
👉 You can analyse headers of any site using [securityheaders.io](https://securityheaders.io).

---

## 🛡️ Content-Security-Policy (CSP)

- Adds an extra layer of defense against **XSS** and code injection.
- Defines which domains/sources are trusted for loading content.
- Common directives:
    - 📌 **default-src 'self'** → Only allow resources from the same domain.
    - 📌 **script-src 'self' [https://cdn.tryhackme.com](https://cdn.tryhackme.com)** → Scripts allowed from self + CDN.
    - 📌 **style-src 'self'** → Stylesheets only from the same domain.

**Example:**

```
Content-Security-Policy: default-src 'self'; script-src 'self' https://cdn.tryhackme.com; style-src 'self'
```

---

## 🌐 Strict-Transport-Security (HSTS)

- Forces browsers to always connect via **HTTPS**.
- Prevents downgrade attacks and insecure connections.
- Directives:
    - ⏳ **max-age=63072000** → Expiry time in seconds (here ~2 years).
    - 🌍 **includeSubDomains** → Apply rule to all subdomains.
    - 🚀 **preload** → Add site to browser preload lists for HSTS enforcement.

**Example:**

```
Strict-Transport-Security: max-age=63072000; includeSubDomains; preload
```

---

## 📄 X-Content-Type-Options

- Prevents browsers from **MIME type sniffing** (guessing content type).
- Ensures only the declared `Content-Type` is respected.

**Directive:**

- 🛑 **nosniff** → Do not guess MIME type.

**Example:**

```
X-Content-Type-Options: nosniff
```

---

## 🔗 Referrer-Policy

- Controls how much **referrer information** is sent when navigating between sites.
- Directives:
    - 🚫 **no-referrer** → No referrer info sent at all.
    - 🏠 **same-origin** → Send referrer only within the same origin.
    - 🔒 **strict-origin** → Send referrer only if protocol stays the same (HTTPS → HTTPS).
    - 📜 **strict-origin-when-cross-origin** → Full referrer for same-origin, origin-only for cross-origin.

**Examples:**

```
Referrer-Policy: no-referrer
Referrer-Policy: same-origin
Referrer-Policy: strict-origin
Referrer-Policy: strict-origin-when-cross-origin
```