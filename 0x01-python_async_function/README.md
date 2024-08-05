# 0x01. Python Async Function

This project involves writing asynchronous Python functions to understand and utilize async/await syntax and manage concurrency. The tasks include creating coroutines, handling multiple coroutines, measuring execution time, and working with asyncio tasks.

## Tasks :page_with_curl:

* **0. The basics of async**
  * [0-basic_async_syntax.py](./0-basic_async_syntax.py): Write an asynchronous coroutine that takes in an integer argument (`max_delay`, with a default value of 10) named `wait_random` that waits for a random delay between 0 and `max_delay` (included and float value) seconds and eventually returns it.
  * Usage: `python3 0-main.py`
  * Returns a random float value after waiting for a random delay between 0 and `max_delay` seconds.
  * Annotations: `max_delay: int = 10`, `return: float`
  * Example:
    ```python
    # 0-main.py
    #!/usr/bin/env python3
    
    import asyncio
    
    wait_random = __import__('0-basic_async_syntax').wait_random
    
    print(asyncio.run(wait_random()))
    print(asyncio.run(wait_random(5)))
    print(asyncio.run(wait_random(15)))
    ```

* **1. Let's execute multiple coroutines at the same time with async**
  * [1-concurrent_coroutines.py](./1-concurrent_coroutines.py): Import `wait_random` from the previous python file that you’ve written and write an async routine called `wait_n` that takes in 2 int arguments (in this order): `n` and `max_delay`. You will spawn `wait_random` n times with the specified `max_delay`.
  * Usage: `python3 1-main.py`
  * Returns a list of all the delays (float values) in ascending order without using `sort()`.
  * Annotations: `n: int`, `max_delay: int`, `return: List[float]`
  * Example:
    ```python
    # 1-main.py
    #!/usr/bin/env python3
    '''
    Test file for printing the correct output of the wait_n coroutine
    '''
    import asyncio
    
    wait_n = __import__('1-concurrent_coroutines').wait_n
    
    print(asyncio.run(wait_n(5, 5)))
    print(asyncio.run(wait_n(10, 7)))
    print(asyncio.run(wait_n(10, 0)))
    ```

* **2. Measure the runtime**
  * [2-measure_runtime.py](./2-measure_runtime.py): From the previous file, import `wait_n`. Create a `measure_time` function with integers `n` and `max_delay` as arguments that measures the total execution time for `wait_n(n, max_delay)`, and returns `total_time / n`. Your function should return a float.
  * Usage: `python3 2-main.py`
  * Returns the average runtime of `wait_n` function.
  * Annotations: `n: int`, `max_delay: int`, `return: float`
  * Example:
    ```python
    # 2-main.py
    #!/usr/bin/env python3
    
    measure_time = __import__('2-measure_runtime').measure_time
    
    n = 5
    max_delay = 9
    
    print(measure_time(n, max_delay))
    ```

* **3. Tasks**
  * [3-tasks.py](./3-tasks.py): Import `wait_random` from `0-basic_async_syntax`. Write a function (do not create an async function, use the regular function syntax to do this) `task_wait_random` that takes an integer `max_delay` and returns an `asyncio.Task`.
  * Usage: `python3 3-main.py`
  * Returns an asyncio.Task.
  * Annotations: `max_delay: int`, `return: asyncio.Task`
  * Example:
    ```python
    # 3-main.py
    #!/usr/bin/env python3
    
    import asyncio
    
    task_wait_random = __import__('3-tasks').task_wait_random
    
    
    async def test(max_delay: int) -> float:
        task = task_wait_random(max_delay)
        await task
        print(task.__class__)
    
    asyncio.run(test(5))
    ```

* **4. Tasks**
  * [4-tasks.py](./4-tasks.py): Take the code from `wait_n` and alter it into a new function `task_wait_n`. The code is nearly identical to `wait_n` except `task_wait_random` is being called.
  * Usage: `python3 4-main.py`
  * Returns a list of all the delays (float values) in ascending order.
  * Annotations: `n: int`, `max_delay: int`, `return: List[float]`
  * Example:
    ```python
    # 4-main.py
    #!/usr/bin/env python3
    
    import asyncio
    
    task_wait_n = __import__('4-tasks').task_wait_n
    
    n = 5
    max_delay = 6
    print(asyncio.run(task_wait_n(n, max_delay)))
    ```
