# 🧪 PortSwigger XSS Lab 01 – Reflected XSS into HTML context with nothing encoded

## 🔍 Lab Description
This lab contains a simple reflected XSS vulnerability in the search functionality.
User input from the search field is reflected directly into the HTML without encoding or sanitization.


🔗 [Lab URL](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded)

## 💣 Payload
```html
<script>alert('0xmust4fa')</script>

Example full URL: https://<your-lab-id>.web-security-academy.net/?search=<script>alert('0xmust4fa')</script>


--> Exploit Strategy
1. Identified that input from the search parameter was directly reflected in the HTML.
2. No encoding applied to < or > characters.
3. Injected a simple <script> tag with alert() to test execution.

✅ Outcome
The browser parsed and executed the injected script — triggering the alert box and solving the lab.

🧠 Lesson Learned
This is a classic case of reflected XSS, where malicious input is reflected directly into the page. When no sanitization or encoding is applied, exploitation is straightforward using a script tag.

