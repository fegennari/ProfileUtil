# ProfileUtil
Simple timing profiler to use in instrumenting C++ code

This utility tracks stats for each call to a named profiler and prints a simple text table with rows for each timer and columns for {name, count, total, max, average}. Here name is the timer name, count is the number of calls to that named timer, total is the total time across calls in milliseconds, max is the max time of any call in ms, and average is the average time per call in ms (total/count).

Just include profiler.h in your code and compile profiler.cpp into your project if you want to use the timing_profiler class to record stats across calls. There are two variants of this class, one which tracks time in milliseconds using integers and the other which tracks sub-ms time using floats. The file profiler.cpp uses global variables for tracking stats, but they can be removed or moved elsewhere in the code in which this utility is used.

To use the profiler, just add a highres_timer_t object at the top of the function or above the code you want to time. This takes a required <name> and optional <enabled> flag to allow the profiling to be toggled on and off with a Boolean variable. The <no_loading_screen> argument is leftover from another project and can be ignored.

For example:
  highres_timer_t timer("my_timer");
  
The highres_timer_t::end() function can be called to end timing at some point in the middle of the code. Otherwise timing will end when the timer goes out of scope and the destructor is called.
