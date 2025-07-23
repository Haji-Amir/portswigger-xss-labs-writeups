🧪 PortSwigger XSS Lab 06 – DOM XSS in jQuery selector sink using a hashchange event
🔍 Lab Description
This lab contains a DOM-based XSS triggered via a hashchange event. The app uses the hash portion of the URL (location.hash) inside a jQuery selector, which becomes exploitable when attacker-controlled content is inserted.

🔗 Lab URL
https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-selector-hash-change-event

💣 Payload (iframe-based delivery)
<iframe src="https://0aea00bf030154ff80ba03b200350057.web-security-academy.net/#"
        onload="this.src+='<img src=x onerror=print()>'">
</iframe>


🛠️ Exploit Strategy
Identified jQuery was using :contains() with unescaped location.hash data.

Created a payload that breaks out of the selector string and injects an image tag with an onerror handler.

Delivered the payload via the exploit server using an iframe to trigger hashchange automatically.

✅ Outcome
The payload caused the browser’s print dialog to appear (print() executed), and the lab was marked as solved.

🧠 Lesson Learned
Using unescaped input inside jQuery selectors (especially :contains()) is extremely dangerous. Always sanitize input and avoid using jQuery selectors for user content.

![Lab Screenshot](./screenshots/Lab-06-DOM-XSS-01.png)
![Lab Screenshot](./screenshots/Lab-06-DOM-XSS-02.png)
![Lab Screenshot](./screenshots/Lab-06-DOM-XSS-03.png)
![Lab Screenshot](./screenshots/Lab-06-DOM-XSS-04.png)