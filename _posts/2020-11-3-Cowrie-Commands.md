---
layout: post
title:  "Cowrie-Commands"
by:     "Michael Meade"
---
# gzip downloaded file mod date grabber 
`file * | grep "gzip" | cut -d "," -f 2  | cut -d ":" -f 1,2,3,4,5 | sort | uniq -c | sort -bgr | head -n 10`

