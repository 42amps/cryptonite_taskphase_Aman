# Stored XSS into HTML context with nothing encode

Stored cross site scripting is also known as Secondary XSS.
The difference between Stored XSS and Reflected XSS is just that 
reflected is immediately executed and the stored attack persists in 
the database until its manually removed.

The key difference is persistence and scale of impact.

For example, If i were to comment `<h1> Hello Cryptonite </h2>`

![image](https://github.com/user-attachments/assets/0a896313-7d5b-41e1-bc8d-2b93649fab38)

Notice how we dont see `h1`, we actually see that html has been passed as valid html.
Which further proves that there's a vulnerability.

So we can inject some javascript here:
`<script> alert('Cryptonite') </script>`
Now the advantage of stored XSS is that essentially anyone who visits this blog is going to
be victim of this attack.

![image](https://github.com/user-attachments/assets/09459317-8637-43b2-9e11-7549591c10c9)
