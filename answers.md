#!/bin/bash
## Task 1

Command:
grep -E -c '^[^#]' firewall.log

Result:
100000

Explanation:
The ^ anchor matches the beginning of a line. [^#] matches any line that does not start with #, excluding the header lines and counting only firewall events.
