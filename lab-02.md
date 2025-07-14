# 🧪 PortSwigger XSS Lab 02: Stored XSS into HTML context with nothing encoded

## 🔍 Lab Description
This lab contains a stored XSS vulnerability in the comment section of a blog post.
User input is inserted into the HTML without any sanitization or encoding.
To solve the lab, submit a comment that triggers alert() when the post is viewed.


🔗 [Lab URL](https://portswigger.net/web-security/cross-site-scripting/stored/lab-html-context-nothing-encoded)

## 💣 Payload
```html
<script>alert('0xmust4fa')</script>

--- --- --- --- --- --- --- --- --- --- --- --- --- --- ---

--> Exploit Strategy
1. Navigated to the blog comment form.
2. Submitted the payload in the comment text field.
3. Upon submission, the payload was stored in the system and reflected into the HTML of the blog post.
4. When the post was reloaded, the JavaScript executed automatically.

✅ Outcome
The alert triggered as soon as the blog post loaded with the stored comment — lab marked as solved.

🧠 Lesson Learned
Stored XSS is more dangerous than reflected XSS because the malicious script is persistently stored on the server and affects all users who view the page. This lab highlights the risk of unsanitized input being stored and displayed without proper encoding.