🧪 PortSwigger XSS Lab 03 – DOM XSS via document.write()
🔍 Lab Description
This lab contains a DOM-based XSS vulnerability in the search query tracking functionality.

The vulnerable page uses JavaScript’s document.write() to dynamically insert content from location.search (the URL query string) into the HTML. Because document.write() directly injects untrusted input, it's possible to execute arbitrary JavaScript.

To solve the lab, craft a URL that triggers alert().

🔗 [Lab URL](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink)

## 💣 Payload
```html
"><script>alert('0xmust4fa')</script>

📌 Example full URL: https://<your-lab-id>.web-security-academy.net/?search="><script>alert('0xmust4fa')</script>

--> Exploit Strategy
1. Inspected the page source and identified document.write() being used to write the search parameter (location.search) directly into the DOM.
2. Crafted a payload that breaks out of the existing HTML and injects a <script> tag.
3. Used a reflected payload in the URL, targeting the search parameter.

✅ Outcome
When the page was loaded with the crafted URL, document.write() injected the raw input directly into the HTML, executing the JavaScript and triggering the alert — lab solved.

🧠 Lesson Learned
DOM XSS occurs entirely on the client-side when JavaScript handles untrusted input insecurely.
Using functions like document.write() or innerHTML without validation/sanitization can lead to easy exploitation.
