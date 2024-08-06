# 0x02. Python Async Comprehension

This project focuses on writing asynchronous Python functions and using asynchronous comprehensions to handle async iterables. The tasks involve creating async generators, using async comprehensions, and measuring runtime for parallel executions.

## Tasks :page_with_curl:

* **0. Async Generator**
  * [0-async_generator.py](./0-async_generator.py): Python coroutine that loops 10 times, each time asynchronously waits 1 second, then yields a random number between 0 and 10.
  * Usage: `python3 0-main.py`
  * Annotations: `yield: float`

* **1. Async Comprehensions**
  * [1-async_comprehension.py](./1-async_comprehension.py): Python coroutine that collects 10 random numbers using an async comprehension over `async_generator`, then returns the 10 random numbers.
  * Usage: `python3 1-main.py`
  * Annotations: `return: List[float]`

* **2. Run time for four parallel comprehensions**
  * [2-measure_runtime.py](./2-measure_runtime.py): Python coroutine that executes `async_comprehension` four times in parallel using `asyncio.gather`, measures the total runtime, and returns it.
  * Usage: `python3 2-main.py`
  * Annotations: `return: float`

