# DOM XSS in jQuery
There's a DOM XSS vulnerability in the feedback functionality where the `returnPath` parameter from the URL is being directly reflected into the href attribute of a link using jQuery's `$` selector and no encoding is done which proves to be a vulnerability for us to exploit.

whatever value was in `returnPath` got placed directly into the href of the link with the id backLink

## Exploitation:

Now that we understood how the parameter worked, I injected a simple JavaScript payload into the `returnPath` : `javascript:alert(document.cookie)` making it 
`https://0a7d00000319d7f3821a702800280057.web-security-academy.net/feedback?returnPath=javascript:alert(document.cookie)`

![image](https://github.com/user-attachments/assets/3e5145fd-303d-4327-b2e6-b46d486d321c)

