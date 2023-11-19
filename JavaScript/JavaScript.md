#  JavaScript

Initially JavaScript used to be interpreted language, as when web browsers used
to come across JavaScript, they used to interpret it line by line and execute it
on the fly.

## Just In Time Compilation

Nowadays we have JavaScript engines like :
- V8 in Chrome
- SpiderMonkey in Firefox
- JavaScriptCore in Safari

These modern JavaScript engines employ a just-in-time (JIT) compilation process.
When code is compiled, then compiler converts source code into machine code and then
the generated machine code is executed. This process makes execution fast but startups
are slow due to time it takes for compilation.
Startup time is fast with interpreted languages as there the code is simply translated
and executed line by line. Problem with interpretation is that for any code which
lets say is getting repeated multiple times for example say in a loop then this
whole interpretation is going again and again which becomes inefficient.

Just In Time Compilation aims to fix this interpreter’s inefficiency. JITs will
have a monitor or profiler which while code is getting executed by the interpreter
will keep track of how many times the different statements get hit. This way it
will detect parts of code being used most and those can be compiled and stored.

