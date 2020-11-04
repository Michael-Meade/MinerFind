---
layout: post
title:  "Cowrie-Commands"
by:     "Michael Meade"
---
# gzip downloaded file mod date grabber 
`file * | grep "gzip" | cut -d "," -f 2  | cut -d ":" -f 1,2,3,4,5 | sort | uniq -c | sort -bgr | head -n 10`

# get not stripped files
`file * | grep "not" | awk  ' {print $1 }' | cut -d ':' -f 1`

# Get uniq bash script's that was downloaded on the honey pot
`cat cowrie.json* | jq '. | select(.eventid | contains("cowrie.session.file_download")) .destfile' | grep ".sh" | grep -v ".ssh"  | sort | uniq`


# top 10 downloaded files - removes null & duplicates
`cat cowrie.json* | jq '. | select(.eventid | contains("cowrie.session.file_download")) .destfile' | grep -v "duplicate" | grep -v "null"  | sort | uniq -c | sort -bgr | head -n 10`
