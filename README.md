# README

This is a repository to show the impact of scripts like respond.js on website performance.

This has been done by analysing the network-panels of the browsers (Firebug, Chrome DevTools, Dynatrace AJAX Edition for IE8).

__NOTE: Some results are written conclusions based on some statistics and my thoughts on that. So this might have errors but shouldn't normally.__

# Conclusion:

- If you're using respond.js you have *1 additional HTTP-Request*.
- If you're using respond.js you have *2kb additional filesize*
- If you're using respond.js you might expericence *lacks on loadtime* when using IE≤8 and *more than 3 external files in head*.
- If you're using respond.js you might expect increasement of about *1-50ms on pageload in modern browsers* (Chrome, Firefox)
- If you're using respond.js you might expect increasement of about *50-120ms on pageload in older browsers* (tested in IE8)