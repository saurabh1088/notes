#  OS Log

## Apple’s Unified logging APIs

import os
os module define new Logging APIs introduced with Xcode 12

- log messages are different from print statement in a key way. Log message is not 
fully converted into a string as that would be very slow. Instead the compiler 
and logging library work together to produce a heavily optimized represenataion 
of log message leveraging the type of the log data

- With optimized representation you pay the cost of converting to a string only 
when the log message is actually displayed

- log messages can contain a wide variety of data types

- To add a custom type to log message all one need to do is to make it conformable 
to protocol CustomStringConvertible

- Nonnumeric values are redacted by default, a value can be made to be printed by 
passing an optional parameter for privacy in log

Five log levels, in increasing order of their importance
- Debug
- Info
- Notice (Default)
- Error
- Fault

### Persistence

Only logs that are persisted can be retrieved after execution.
Persistence depends on log levels, persistence increases with the log level importance

- Debug : Not persisted
- Info : Persisted only during log collect
- Notice : Persisted up to a storage limit
- Error : Persisted up to a storage limit
- Fault : Persisted up to a storage limit

This persistence is on the device. One can use log collect to get logs from device 
to MacBook

### Performance

- Logging has a effect on performance. Even though in general it has low overhead.

- Log levels have different performance relative to each other. Less important levels are faster.

- Fault level is the slowest, debug level is the most performant. 

- Logging at the debug level is so fast because debug messages are not persistet 
at all. Debug messages are discarded when the logs aren’t being streamed. 

- Swift also optimizes so that debug level messages code is not even executed if 
not required. This means one can use verbose message debug level and use expensive 
functions to construct messages.

### Formatting

Formatting log data for improved readability

One can align a data. One can use optional format and align parameters for this
Formatting doesn’t adds any performance overhead to logging

Personal data must not be public, so those must not be marked .public as logs 
can be accessed by anyone having physical access to device.

For masking one can also use hash, which gives a benefit over using private that 
one can compare hashes of a sensitive data to track where same data is used without 
exposing it.
