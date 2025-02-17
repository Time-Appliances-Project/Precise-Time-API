## Precise Time API


# Background

The concept of temporal ordering of events pervades our thinking about systems [10]. When we use physical clocks to order events, if event A happened at an earlier time than event B, the timestamp of A should be lower than the timestamp of B. Unfortunately, even with accurate and precise physical clocks, this is not always possible. We can only order events when the distance between timestamps exceeds the maximum error of the measurement. To order events correctly, we must account for the measurement error.
In existing time APIs [1], time is encoded as an offset from an epoch. The epoch in Unix is Jan 1st, 1970 [2], and in Windows, it is Jan 1st, 1601 [3]. In both cases, time is represented as an exact value with no information about the error that may have been introduced by the time measurement and synchronization processes.
Today, time management technologies [4][5] not only expose the time as an offset from an epoch but also the error between the reference clock and the synchronized clock. This error represents the time uncertainty at the synchronized clock, which is never zero. It is a result of accumulated imprecisions in the network equipment, uncertainties in the OS scheduler, and differences in the supported libraries.

# Problem Statement
Precise time is represented as an offset from an epoch and is accompanied by an upper bound of accumulated error. Unfortunately, many time APIs ignore the error, making it difficult to confidently order events based on their timestamps.
To make effective use of precise time in applications and services, we need a better API that exposes the clock time, the uncertainty window, and data from the synchronization process to the application. This information is critical for accurately ordering events and improving the reliability of time-sensitive systems.
![image](https://github.com/user-attachments/assets/9a855e81-90d4-4bbd-b49d-2e35b09443e9)
