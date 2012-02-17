# CONSIDERATIONS


## preamble

"+Anselm Hannemann, first up i'm interested in testing the performance impact of something like Respond.js. It requires being in the head, XHRs all your stylesheets, parses them and injects new styles. I can't believe this is a trivial amount of time, but I haven't seen it quantified. 
Of course this has to be tested against real world sites and not cheap test pages." (Paul Irish, Google+)

### 1st result (not statistically):

There's indeed a delay on the other scripts executed after the respond.js call. I don't have statistics yet but will try to get some consitency in it to do a graph.

### 2nd result 

I've tested on some sites and came around that respond.js itself doesn't hurt performance "much". Even if it's linked as normal external script (no ext. domain) it doesn't hurt performance very much in modern browsers like Chrome or Firefox as they download the scripts in parallel (in that case modernizr and respond). Tested on three normal live-sites. (…)
But surely you have 1 more request, 2.2kb more to load and DOM content load time is about 1ms-50ms increased (50 at ext. domain, 1-5ms ext same domain). But pageLoad is less linked as script on ext. domain. Execution time of the script itself took between 80-100ms, response latency is at 80-100ms.
So if you use respond.js inside other scripts like inside of Modernizr it wouldn't hurt performance very much, especially when serving via ext. cookie-less domain.

### 3rd results

IE8 tries to download in parallel but fails a bit. So we have a mini loss of some milliseconds in IE8 when using respond.js - this is the time to first-byte loading respond.js (same server, no CDN). CSS is loaded before.
But modernizr (follows up immediately in html) is loaded with a delay of about 50-100ms as IE8 seems to only can handle 3 files in parallel. When first-file is finished, next file in queue is starting. So there might me a big impact on performance when using respond.js and using more than 3 external files.

### 4th results:

In IE8, respond.js takes about 80-120ms additional rendering time. It requires a bit more CPU usage (not much).

---------------

## NOTE: This results are written conclusions based on some statistics and my thoughts on that. So this might have errors but shouldn't normally.

# Conclusion:

- If you're using respond.js you have 1 additional HTTP-Request.
- If you're using respond.js you have 2kb additional filesize
- If you're using respond.js you might expericence major lacks on loadtime when using IE≤8 and more than 3 external files in head.
- If you're using respond.js you might expect increasment of about 1-50ms on pageload in modern browsers (Chrome, Firefox)
- If you're using respond.js you might expect increasment of about 50-120ms on pageload in older browsers (tested in IE8)