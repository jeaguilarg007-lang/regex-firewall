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

## Task 3

Command:
grep -E -c ' 11\.' firewall.log

Result:
33217

Explanation:
The sequence \. escapes the dot character, so it is treated as a literal period instead of matching any character. The regex counts events whose source IP address begins with 11.

## Task 4

Command:
grep -E -c '[0-9]{7}$' firewall.log

Result:
2343

Explanation:
The character class [0-9] matches any digit and {7} requires exactly seven digits. The $ anchor ensures that the seven-digit number is at the end of the line, which corresponds to the size field.

## Task 5

Command:
grep -E '^[0-9]{4}-' firewall.log | sed -E 's/^([0-9-]+) [0-9:]+ ([A-Z]+) ([A-Z]+) .*/\1 \2 \3/' | head -5

Result:
2018-05-25 FORWARD TCP
2018-02-22 FORWARD UDP
2018-03-20 REJECT UDP
2018-11-08 REJECT TCP
2018-07-24 REJECT TCP

Explanation:
The command first filters event lines that start with a date. Then sed uses capture groups to extract the date, action, and protocol fields and backreferences (\1, \2, \3) to rebuild the output.