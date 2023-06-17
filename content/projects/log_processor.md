---
title: Distributed Log File Processor
summary: A parallel distributed system to analyze large log files Hadoop(Scala) and AWS EMR .
author: Oct 2022 - Nov 2022
weight: 2
---

`Scala` `AWS EC2` `AWS S3` `AWS EMR` `gRPC`
`Hadoop` `REST` `AWS Lambda` `slf4j`

- Developed a program to determine the distribution of log messages that match a specific pattern across various log files, message types, and time intervals.

- Given log files of the format as input

```
09:58:55.569 [main] INFO  GenerateLogData$ - Log data generator started...
09:58:55.881 [scala-execution-context-global-17] INFO  GenerateLogData$ - NL8Q%rvl,RBHq@|XR2U&k>"SXwcyB#iv
09:58:55.928 [scala-execution-context-global-17] WARN  Generation.Parameters$ - =5$YcP!s@h
09:59:30.849 [scala-execution-context-global-17] INFO  Generation.Parameters$ - V<Z~#Ws"WNJ:[d?+dRpaIFp23"1_oKn;Qd,>
09:59:30.867 [scala-execution-context-global-17] INFO  Generation.Parameters$ - 3FNgL<)k7+c+8yQ"3m*e#!)HK[['z+-an/Uw?J'|[<w&kbtM
09:59:30.876 [scala-execution-context-global-17] ERROR  Generation.Parameters$ - +5l}CAK:}q])
09:59:30.891 [scala-execution-context-global-17] INFO  Generation.Parameters$ - Mv8)!{uuaD3%<m.VO/[pfHLS&eIBmKx~(6
```

the program uses `AWS EMR` to output CSV files with the following statistics:

1. distribution of different types of messages across predefined time intervals matching a regex pattern.
2. time intervals sorted in the descending order that contained most log messages of the type `ERROR` also matching a regex pattern.
3. number of the generated log messages for each _**message type**_ .
4. number of characters in each log message matching a regex pattern.
