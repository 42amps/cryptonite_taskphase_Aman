# DOM XSS in jQuery with hashchange Event
Okay so this one gets messy as we dive deep into its rabbit hole.

`<script>
    $(window).on('hashchange', function(){
        var post = $('section.blog-list h2:contains(' + decodeURIComponent(window.location.hash.slice(1)) + ')');
        if (post) post.get(0).scrollIntoView();
    });
</script>
`

Here's whats happening:
- The page has a `hashchange` event listener.
- When the URL's hash changes, the script decodes the hash `decodeURIComponent(window.location.hash.slice(1))` looks for a matching blogpost title in `section.blog-list h2`
  and then scrolls to it.

THis jQuery is vulnerable to injecting HTML tags with JS because the hash value isn't sanitized.
So our task is to craft a payload that uses this to call the print() function.

## Exploitation:
Now we couldve used a simple payload like `<img src=1 onerror=print()>` but here's the catch:
The hashchange event doesn't trigger unless we refresh or manipulate the URL multiple times.

After some research i have found a workaround to automate the process using an inline frame.
An `inline` frame allows embedding one webpage within another. So its like a mini browser window inside a page and we can use it to dynamically load URLs and trigger events such as hashchange.

Here's a revised payload:

`<iframe src="https://0ad0009003cb916a816ef7680027006a.web-security-academy.net/#" onload="this.src += '<img src=1 onerror=print()>'"></iframe>`

![image](https://github.com/user-attachments/assets/f3edb61e-80a2-4271-8704-86d3588fbcfb)

![image](https://github.com/user-attachments/assets/8967e2bb-64f7-48c8-86d7-33dc640e28f6)
