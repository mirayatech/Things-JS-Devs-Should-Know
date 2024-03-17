
# Security Practices in JavaScript Applications

Understanding and preventing common security vulnerabilities like Cross-Site Scripting (XSS) and Cross-Site Request Forgery (CSRF) are crucial for developing secure JavaScript applications.

## Cross-Site Scripting (XSS)

XSS is a vulnerability that allows attackers to inject malicious scripts into content served to users, potentially stealing data or impersonating the user.

### Preventing XSS

- **Escaping User Input**: Transform user input to safely render HTML content.

```javascript
function escapeHTML(text) {
    return text.replace(/&/g, "&amp;")
               .replace(/</g, "&lt;")
               .replace(/>/g, "&gt;")
               .replace(/"/g, "&quot;")
               .replace(/'/g, "&#039;");
}
```

- **Content Security Policy (CSP)**: Restrict sources of content to prevent script injections.

```html
<meta http-equiv="Content-Security-Policy" content="default-src 'self'; script-src 'self'">
```

## Cross-Site Request Forgery (CSRF)

CSRF tricks users into submitting malicious requests, exploiting the trust a web application has in the user's browser.

### Preventing CSRF

- **Anti-CSRF Tokens**: Use unique tokens that are validated server-side with each request.

```html
<input type="hidden" name="csrf_token" value="{{ csrf_token }}">
```

- **SameSite Cookie Attribute**: Control how cookies are sent with cross-site requests to mitigate CSRF attacks.

```javascript
res.cookie('sessionId', 'your_session_id', { httpOnly: true, sameSite: 'Strict' });
```
