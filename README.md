# UNDER CONSTRUCTION

This is a blog.  It is a work in progress.  Like me.  Check out my bio if, by some strange chance, you landed here and are in cyber security.  Give me a follow.  I have lots of things planned for this blog:

+ Tool Reviews
+ Vulnerability Trend Analyses
+ Threat Actor Trends
+ Things I Find Interesting (OffSec Related)

# Musings

I found an interesting endpoint / parameter today on a target.  We'll just say it was this:

`example.com/group?gid=123&referrer=4321#/`

The `referrer` parameter was optional, but when absent the button on the page to "Go Back To Referrer" button would disappear.  I wanted to figure out the full extent of what this parameter controlled.  I started with throwing a large number in, 100000000000000000 just to see what happened.  Status 500'd... Well this might be good!

With that I began looking at the Inspector, I found in the HTML where the code eneded up.  The target uses React, so when I saw this living in an `<a>` tag within an `href` element, my heart skipped a beat.

A bit lower I saw that the referrer's name was printed to the page in the button.  Knowning this target a bit more in depth, I've checked and the user name field is limited to a small amount of characters, and prevents most special characters.  This might have been a good place to test Stored XSS, but this control removes that threat from this attack vector.

I got busy, now that I found a couple places where this parameter controlled, with fuzzing.  I used the following lists:

~~~
123abc
0x50
'50'
"50"
50.5
-50
+50
null
undefined
[]
{}
true
false
<script>alert(1)</script>
javascript:alert(1)
data:text/html,<script>alert(1)</script>
" onmouseover="alert(1)
' onerror="alert(1)"
<svg/onload=alert(1)>
%00
%0a
%0d
%23 (URL fragment break: #)
%3cscript%3ealert(1)%3c/script%3e
%3Cimg%20src%3Dx%20onerror%3Dalert(1)%3E
~~~

I also used this:
~~~
999999999999999
-1
1e1000
NaN
Infinity
0xFFFFFFFF
0b101010
~~~

The first list found some more 500's, but for the most part the application just removed the entire payload.  The second list, and some of the first list, showed that it was looking purely for an integer value.  It had to be non-negative (so -50 gave a server error), and it cut decimal places (no rounding, just straight cut).

I might have ended up getting silly with some manual testing of special characters and some basic payloads, like `{{7*7}}` just to see what happens but it ignored anything within any type of brackets.

That's the excitement of about 20 minutes at the end of my work day.  The thing I'm going to go back to this and try is DOM XSS.  The fact this dynamically writes to the document and lives in the href element of and `a` tag gives me some hope it might be `dangerouslySetInnerHTML` at play.  Even with my fuzzing pointing to any non-numeric characters are sanitized, there might be a way to bypass I'm not considering...

## TODO: A lot...
1. Write my first blog
2. Finalize the about.md
3. Polish the layout
4. Update the style?
5. Market

<h2>Testing H2</h2>

`Testing Keywords`

Testing Code Blocks
~~~js
<img src=x>
~~~
