# DOM XSS 
DOM based XSS is where user input from a search parameter is passed to 
`document.write` without sanitization.

The website here uses `document.write` to dynamically write content to the webpage.
This allows us to inject and execute javascript.

![image](https://github.com/user-attachments/assets/a3cbece9-b10a-48ed-8334-e9d8394b46af)

The search parameter is reflected on the page via Javascript through `document.write`
and since `document.write` executes raw HTML/Javascript, we can craft a payload accordingly.

Since this happens during page load, we can inject an `onload` event handler into an HTML element
to execute javascript.

`Cryptnite" onload="alert('Cryptonite')`

![image](https://github.com/user-attachments/assets/72314d91-170d-4012-9134-b5e43e67635b)
