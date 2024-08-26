# 0x03. Unittests and Integration Tests

This project involves writing unittests and integration tests for Python code. The tasks cover parameterization, mocking, and testing various aspects of the code to ensure it behaves as expected.

## Tasks :page_with_curl:

* **0. Parameterize a unit test**
  * **[test_utils.py](./test_utils.py):** Familiarize yourself with the `utils.access_nested_map` function. Write the first unit test for `utils.access_nested_map` by creating a `TestAccessNestedMap` class that inherits from `unittest.TestCase`.
    * **Methods:**
      * `TestAccessNestedMap.test_access_nested_map`: Decorate this method with `@parameterized.expand` to test the function with the following inputs:
        * `nested_map={"a": 1}, path=("a",)`
        * `nested_map={"a": {"b": 2}}, path=("a",)`
        * `nested_map={"a": {"b": 2}}, path=("a", "b")`
      * Use `assertEqual` to verify the function returns the expected result.
    * **Usage:**
      ```python
      class TestAccessNestedMap(unittest.TestCase):
          @parameterized.expand([
              ({"a": 1}, ("a",), 1),
              ({"a": {"b": 2}}, ("a",), {"b": 2}),
              ({"a": {"b": 2}}, ("a", "b"), 2),
          ])
          def test_access_nested_map(self, nested_map, path, expected):
              self.assertEqual(access_nested_map(nested_map, path), expected)
      ```

* **1. Parameterize a unit test**
  * **[test_utils.py](./test_utils.py):** Implement `TestAccessNestedMap.test_access_nested_map_exception`. Use the `assertRaises` context manager to test that a `KeyError` is raised for the following inputs:
    * `nested_map={}, path=("a",)`
    * `nested_map={"a": 1}, path=("a", "b")`
  * Also, verify that the exception message is as expected.

* **2. Mock HTTP calls**
  * **[test_utils.py](./test_utils.py):** Familiarize yourself with the `utils.get_json` function. Define a `TestGetJson(unittest.TestCase)` class and implement the `TestGetJson.test_get_json` method.
    * **Mocking:**
      * Use `unittest.mock.patch` to patch `requests.get` to return a `Mock` object with a `json` method that returns `test_payload`.
      * Parameterize the method with the following inputs:
        * `test_url="http://example.com", test_payload={"payload": True}`
        * `test_url="http://holberton.io", test_payload={"payload": False}`
    * Test that the mocked `get` method was called exactly once with `test_url` as the argument and that the output of `get_json` matches `test_payload`.

* **3. Parameterize and patch**
  * **[test_utils.py](./test_utils.py):** Read about memoization and familiarize yourself with the `utils.memoize` decorator. Implement the `TestMemoize(unittest.TestCase)` class with a `test_memoize` method.
    * **Class Definition:**
      ```python
      class TestClass:
          def a_method(self):
              return 42

          @memoize
          def a_property(self):
              return self.a_method()
      ```
    * **Mocking:** Use `unittest.mock.patch` to mock `a_method`. Test that when calling `a_property` twice, the correct result is returned but `a_method` is only called once using `assert_called_once`.

* **4. Parameterize and patch as decorators**
  * **[test_client.py](./test_client.py):** Familiarize yourself with the `client.GithubOrgClient` class. Implement a `TestGithubOrgClient(unittest.TestCase)` class with a `test_org` method.
    * **Decorators:**
      * Use `@patch` as a decorator to ensure `get_json` is called once with the expected argument without executing it.
      * Use `@parameterized.expand` to parametrize the test with the following inputs:
        * `"google"`
        * `"abc"`

* **5. Mocking a property**
  * **[test_client.py](./test_client.py):** Read up on how to mock a property. Implement the `test_public_repos_url` method to unit-test `GithubOrgClient._public_repos_url`.
    * **Mocking:** Use `patch` as a context manager to patch `GithubOrgClient.org` and make it return a known payload. Test that the result of `_public_repos_url` is as expected based on the mocked payload.

* **6. More patching**
  * **[test_client.py](./test_client.py):** Implement `TestGithubOrgClient.test_public_repos` to unit-test `GithubOrgClient.public_repos`.
    * **Mocking:**
      * Use `@patch` as a decorator to mock `get_json` and make it return a payload of your choice.
      * Use `patch` as a context manager to mock `GithubOrgClient._public_repos_url` and return a value of your choice.
    * Test that the list of repos matches the expected payload and that the mocked property and `get_json` were called once.

* **7. Parameterize**
  * **[test_client.py](./test_client.py):** Implement `TestGithubOrgClient.test_has_license` to unit-test `GithubOrgClient.has_license`.
    * **Parameterization:** Parametrize the test with the following inputs:
      * `repo={"license": {"key": "my_license"}}, license_key="my_license"`
      * `repo={"license": {"key": "other_license"}}, license_key="my_license"`
    * Also, parameterize the expected returned value.

* **8. Integration test: fixtures**
  * **[test_client.py](./test_client.py):** Create the `TestIntegrationGithubOrgClient(unittest.TestCase)` class and implement `setUpClass` and `tearDownClass`.
    * **Parameterization:** Use `@parameterized_class` to decorate the class and parameterize it with fixtures found in `fixtures.py`. The file contains:
      * `org_payload`, `repos_payload`, `expected_repos`, `apache2_repos`
    * **Mocking:** In `setUpClass`, mock `requests.get` to return example payloads from the fixtures. Use `patch` to start a patcher named `get_patcher`, using `side_effect` to ensure the mock of `requests.get(url).json()` returns the correct fixtures based on the anticipated `url` values.
    * **Tear Down:** Implement `tearDownClass` to stop the patcher.

* **9. Integration tests**
  * **[test_client.py](./test_client.py):** Implement the `test_public_repos` method to test `GithubOrgClient.public_repos`.
    * Ensure the method returns the expected results based on the fixtures.
    * Implement `test_public_repos_with_license` to test `public_repos` with the argument `license="apache-2.0"` and ensure the result matches the expected value from the fixtures.
