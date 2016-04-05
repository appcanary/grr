---
title: will_paginate 3.0.5
date: 2016-03-17
tags: will_paginate, No bugs found
author: team
published: true
layout: post
---
[will_paginate](https://github.com/mislav/will_paginate)
Latest version reviewed: 3.0.5

Summary: No exploitable vulnerabilities found.

Notes from researcher:
We tested for cross-site scripting, shell injection, eval-based command injection, regular expression flaws leading to unsanitized user input and logic errors allowing unsafe user input. The attack surface for will\_paginate is fairly small in that there is only one location where an end-user can pass input to a function. Further, will\_paginate does not utilize serialization or marshaling.

will_paginate was the subject of an XSS via CVE-2013-6459, and so Dylan sought to first eliminate any other XSS venues. After exhausting all input rendering venues, Dylan was satisfied that the renderer successfully prevents unsafe input from being passed along.

He then looked into command injection; initially promising uses of class_eval() and send() were discovered to either not take input or restrict it to Fixnum, rendering it unexploitable.

Finally, he turned his attention towards shell injection or file traversal bugs and was unable to find any exploitable instances of either.

