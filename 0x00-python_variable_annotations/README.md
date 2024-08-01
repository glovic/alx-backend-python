# 0x00. Python Variable Annotations

This project focuses on writing type-annotated Python functions. Type annotations provide a way to indicate the type of a value or variable and can be used for type checking.

## Tasks :page_with_curl:

* **0. Basic annotations - add**
  * [0-add.py](./0-add.py): Python function that takes two floats and returns their sum as a float.
  * Usage: `python3 0-main.py`
  * Returns the sum of `a` and `b` as a float.
  * Annotations: `a: float`, `b: float`, `return: float`

* **1. Basic annotations - concat**
  * [1-concat.py](./1-concat.py): Python function that concatenates two strings and returns the result.
  * Usage: `python3 1-main.py`
  * Returns the concatenated string of `str1` and `str2`.
  * Annotations: `str1: str`, `str2: str`, `return: str`

* **2. Basic annotations - floor**
  * [2-floor.py](./2-floor.py): Python function that returns the floor of a float.
  * Usage: `python3 2-main.py`
  * Returns the floor of `n` as an integer.
  * Annotations: `n: float`, `return: int`

* **3. Basic annotations - to string**
  * [3-to_str.py](./3-to_str.py): Python function that converts a float to its string representation.
  * Usage: `python3 3-main.py`
  * Returns the string representation of `n`.
  * Annotations: `n: float`, `return: str`

* **4. Define variables**
  * [4-define_variables.py](./4-define_variables.py): Defines and annotates variables with specific values.
  * Usage: `python3 4-main.py`
  * Variables:
    - `a` as an integer with value `1`
    - `pi` as a float with value `3.14`
    - `i_understand_annotations` as a boolean with value `True`
    - `school` as a string with value `"Holberton"`
  * Annotations: `a: int`, `pi: float`, `i_understand_annotations: bool`, `school: str`

* **5. Complex types - list of floats**
  * [5-sum_list.py](./5-sum_list.py): Python function that returns the sum of a list of floats.
  * Usage: `python3 5-main.py`
  * Returns the sum of the floats in `input_list`.
  * Annotations: `input_list: List[float]`, `return: float`

* **6. Complex types - mixed list**
  * [6-sum_mixed_list.py](./6-sum_mixed_list.py): Python function that returns the sum of a list of integers and floats.
  * Usage: `python3 6-main.py`
  * Returns the sum of the integers and floats in `mxd_lst`.
  * Annotations: `mxd_lst: List[Union[int, float]]`, `return: float`

* **7. Complex types - string and int/float to tuple**
  * [7-to_kv.py](./7-to_kv.py): Python function that returns a tuple with a string and the square of an int/float.
  * Usage: `python3 7-main.py`
  * Returns a tuple where the first element is `k` and the second element is the square of `v`.
  * Annotations: `k: str`, `v: Union[int, float]`, `return: Tuple[str, float]`

* **8. Complex types - functions**
  * [8-make_multiplier.py](./8-make_multiplier.py): Python function that returns a function which multiplies a float by a given multiplier.
  * Usage: `python3 8-main.py`
  * Returns a function that multiplies a float by the `multiplier`.
  * Annotations: `multiplier: float`, `return: Callable[[float], float]`

* **9. Let's duck type an iterable object**
  * [9-element_length.py](./9-element_length.py): Python function that returns a list of tuples where each tuple contains an element and its length.
  * Usage: `python3 9-main.py`
  * Returns a list of tuples where each tuple contains an element from `lst` and its length.
  * Annotations: `lst: Iterable[Sequence]`, `return: List[Tuple[Sequence, int]]`

* **10. Duck typing - first element of a sequence**
  * [100-safe_first_element.py](./100-safe_first_element.py): Python function that returns the first element of a sequence or `None` if the sequence is empty.
  * Usage: `python3 100-main.py`
  * Returns the first element of `lst` or `None` if `lst` is empty.
  * Annotations: `lst: Sequence[Any]`, `return: Union[Any, None]`

* **11. More involved type annotations**
  * [101-safely_get_value.py](./101-safely_get_value.py): Python function that returns the value for a given key in a dictionary or a default value if the key is not present.
  * Usage: `python3 101-main.py`
  * Returns the value for `key` in `dct` or `default` if the key is not present.
  * Annotations: `dct: Mapping`, `key: Any`, `default: Union[T, None]`, `return: Union[Any, T]`

* **12. Type Checking**
  * [102-type_checking.py](./102-type_checking.py): Python function that returns a zoomed-in version of a tuple based on a factor.
  * Usage: `python3 102-main.py`
  * Returns a zoomed-in version of `lst` based on the `factor`.
  * Annotations: `lst: Tuple`, `factor: int`, `return: List`

