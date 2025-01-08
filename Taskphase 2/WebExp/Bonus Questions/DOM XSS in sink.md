# DOM based XSS using innerHTML
Well this one uses an `innerHTML` assignment which changes the HTML content
of div using the source as `location.search`

So oberving the result when i test search first, We notice `document.getElementById('searchMessage').innerHTML = query`

![image](https://github.com/user-attachments/assets/c385bad7-be68-425e-a46f-4bf3f838f9f0)

So when we try injecting a payload `<script>alert('Cryptonite')</script>` directly as previous challenge,
We notice that it doesnt seem to work anymore cuz no javascript was executed there.

![image](https://github.com/user-attachments/assets/d440441f-b418-42f5-b6ca-00185d757f26)

## Why script tags won't work with innerHTML
When you set innerHTML with a string containing a <script> tag, the browser parses and adds the tag to the DOM but does not execute the script. This behavior prevents accidental or malicious execution of scripts.

## Workaround 
We can pass an img tag with a source we know would error out and then attach the onerror attribute equals javascript alert function.

Passing `<img src='0' onerror='alert()'>`

![image](https://github.com/user-attachments/assets/8e64d1b3-cfac-4ae3-a5cd-4b0f65194311)

So we're exploiting the event error handler which triggers when the image fails to load showing an error in the form of alert function and it works like a charm.
