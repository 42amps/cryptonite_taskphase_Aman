# Reflected XSS into HTML with nothing encoded

Our goal is to exploit a reflected XSS vulnerability in the search functionality of a web app. The app takes user input from the search parameter and reflects it in the HTML response without encoding or sanitization which creates an opportunity for XSS.

## Here's something to observe: 

So I searched for `<h1> YO CRYPTONITE </h2>`

![image](https://github.com/user-attachments/assets/a9872d90-71fe-4df6-90f0-4cc7b24697c9)

Notice how my search term is appearing on another line as a header? this confirms the vulnerability.

So we just have to inject a simple XSS payload: 
`<script>alert('cryptonite')</script>`

![image](https://github.com/user-attachments/assets/7550e9cf-1ce7-4928-a97b-d293a0697fe3)

Now after reloading the page, alert box is triggered which therefore comfirms the vulnerability
