#!/bin/bash
## Task 1

Command:
grep -E -c '^[^#]' firewall.log

Result:
100000

Explanation:
The ^ anchor matches the beginning of a line. [^#] matches any line that does not start with #, excluding the header lines and counting only firewall events.

## Task 2

Command:
grep -E -c ' (DROP|REJECT) ' firewall.log

Result:
60156

Explanation:
The parentheses create a group and the | operator means OR. The regex matches lines where the action field is either DROP or REJECT, using spaces to ensure the match occurs in the action field.

