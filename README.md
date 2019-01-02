
Demo project for [#2074](https://github.com/facebook/buck/issues/2074).


# 2074

```bash
buckw test app
```

The command fails with the following error:

```text
Command failed with exit code 1.
stderr: Tests/SampleTests.swift:5:18: error: no such module 'App'
@testable import App
```
