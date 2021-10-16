# Advanced Python
Advanced Python tips and tricks. This includes methods in optimising and improving the speed of your Python code.

# Faster Python
## Profiling
### line_profiler
line_profiler is a module for doing line-by-line profiling of functions. kernprof is a convenient script for running either line_profiler or the Python standard library's cProfile or profile modules, depending on what is available.

`line_profiler` is an external package that can be installed by `pip install line_profiler`.

* In order to a profile a specific function, you add a decorator, `@profile`, to the desired function.
* Run `kernprof -l YOURCODE.PY`, this will create a *.lprof file for you which can be viewed by running `python3 -m line_profiler YOURCODE.PY.lprof`

### Resources
* https://uwpce-pythoncert.github.io/SystemDevelopment/profiling.html


