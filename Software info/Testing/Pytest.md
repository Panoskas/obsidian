## What are pytest fixtures?

whatever steps we do in arrange stage and data are known as fixtures. Those are the things that need to test a certain action.

In pytest the fixtures are functions that we define to serve these purpose, we can pass these fixtures to our test functions (test cases) so that they can run and set up the desired state for you to perform the test.

## What are the scopes of pytest fixtures?

Some tests might need network activities like logging into a remote server or database, or if you are writing tests for machine learning models, you might have to train models which might be used by several test cases, in such cases running these fixture functions every time user requests can be time-consuming and computationally expensive.

There are five different scopes:

-   **function:** when the scope is set to function, then the object will be teardown immediately after the requesting test function is terminated. When another test function calls that fixture it will rerun and create a new object. by default, the fixtures will have a function scope.
-   **module:** when the first time a function calls the fixture it will create the object and save it for the usage of test functions in the same module. So if any of the test functions in the same module calls that fixture the cached object will be returned. The object will be torn down after all the tests in that module completes.
-   **class:** the fixture will be executed once per class, it will be reused by all the test functions of that same test class. It will tear down after all the test functions from that class are completed.
-   **package:** fixture will be executed on first request and cached until all the test functions in that class get executed, and will be torn down after that.
-   **session:** this is the broad scope in pytest fixture, whenever we call `pytest` it is known as a session. So fixtures with session scope will be executed and cached on the first request and they will be reused until all the tests are completed.