# Table of Contents
- [Table of Contents](#table-of-contents)
  - [General](#general)
    - [What to include in a bug report?](#what-to-include-in-a-bug-report)
    - [What to include in a test case?](#what-to-include-in-a-test-case)
    - [What is the Testing Pyramid?](#what-is-the-testing-pyramid)
    - [What are levels of Testing?](#what-are-levels-of-testing)
    - [Test Strategy vs Test Plan.](#test-strategy-vs-test-plan)
    - [Test Coverage Metrics](#test-coverage-metrics)
    - [Classification of Different Types of Testing](#classification-of-different-types-of-testing)
  - [pytest](#pytest)
    - [What is a Pytest fixture?](#what-is-a-pytest-fixture)
    - [Explain the `autouse` flag in fixtures.](#explain-the-autouse-flag-in-fixtures)
    - [What are pytest's fixture scopes?](#what-are-pytests-fixture-scopes)
    - [How do you mark a test in Pytest?](#how-do-you-mark-a-test-in-pytest)
    - [What is parameterized testing in Pytest?](#what-is-parameterized-testing-in-pytest)
    - [How do you handle exceptions in Pytest?](#how-do-you-handle-exceptions-in-pytest)
    - [How do you run tests in parallel using Pytest?](#how-do-you-run-tests-in-parallel-using-pytest)
    - [What is the purpose of the conftest.py file in Pytest?](#what-is-the-purpose-of-the-conftestpy-file-in-pytest)
    - [How do you create custom Pytest hooks, and what are some common hooks?](#how-do-you-create-custom-pytest-hooks-and-what-are-some-common-hooks)
  - [References](#references)

## General

### What to include in a bug report?

An effective bug report should contain the following:

- Title/Bug ID
- Environment
- Steps to reproduce a Bug
- Expected Result
- Actual Result
- Visual Proof (screenshots, videos, text) of Bug
- Severity/Priority

---

### What to include in a test case?
In agile software development, test cases are more like outlines than a list of step-by-step instructions for a single test. Test cases can include details on required conditions, dependencies, procedures, tools, and the expected output. 

:bulb: ***Common elements of a test case include:***

- **Title**:  The title of a test case points to the software feature being tested.
- **Description** (including the test scenario): The description summarizes what is being verified from the test.
- **Test script** (if automated): In automated testing, a test script provides a detailed description of data and actions required for each functionality test.
- **Test ID**: Every test case should bear a unique ID that serves as an identifier to the test case. For clarity, test case ID should follow a standard naming convention.
- **Test environment**: The test environment is the controlled setup or infrastructure where software or systems are tested.
- **Notes**: This section includes any relevant comments or details about the test case that do not fit in any other section of the test case template.

### What is the Testing Pyramid?

The pyramid attempts to visually represent a logical organization of testing standards. It consists of three distinct layers.

<p align="center" width="100%">
    <img width="50%" src="https://semaphoreci.com/wp-content/uploads/2022/03/pyramid-progression.webp"> 
</p>

- Unit tests can only find logical errors at the most fundamental level. They are fast and require very few resources to run.
- Integration tests verify that services and databases work well together with the code and the classes you’ve written. They can only find problems at the interfaces where two or more components meet.
- E2E tests depend on the complete application being able to start. These are the most comprehensive type of tests we have and, accordingly, need the most computing resources and time to run.

|                                  time evolution                                  |                                   cost                                    |
| :------------------------------------------------------------------------------: | :-----------------------------------------------------------------------: |
| ![](https://semaphoreci.com/wp-content/uploads/2022/03/pyramid-vs-maturity.webp) | ![](https://semaphoreci.com/wp-content/uploads/2022/03/pyramid-cost.webp) |

---

### What are levels of Testing?

The most common types of testing levels include – unit testing, integration testing, system testing, and acceptance testing. Unit tests focus on individual components, such as methods and functions, while integration tests check if these components work together properly. System tests verify that the entire system meets the functional requirements specified by stakeholders, while acceptance tests validate the software against their criteria for acceptable behavior.

<p align="center" width="100%">
    <img width="60%" src="https://testsigma.com/blog/wp-content/uploads/Levels-of-testing-1.png"> 
</p>

---

### Test Strategy vs Test Plan.

Simply put, both the Test Plan and Test Strategy are essential documents in the testing process, but they serve different purposes and address different levels of detail. The Test Plan focuses on the specifics of testing for a particular project, while the Test Strategy sets the overarching approach and principles for testing across projects or the entire organization.

| Aspect                   | Test Plan                                                                                                                         | Test Strategy                                                                                                                                     |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Definition**           | A Test Plan outlines the approach, scope, objectives, resources, and schedule for testing a specific project or product.          | A Test Strategy defines the high-level approach to testing for an organization or a project, guiding the overall testing process.                 |
| **Scope**                | Focuses on the details of how testing will be carried out for a specific project.                                                 | Encompasses a broader perspective, outlining principles, objectives, and methods to achieve consistent testing across projects.                   |
| **Purpose**              | Provides a detailed roadmap for the testing activities, including what, when, and how to test.                                    | Sets the direction for testing efforts, aligning them with the organization's goals and helping in making important testing decisions.            |
| **Audience**             | Primarily for the project team, including testers, developers, managers, and stakeholders.                                        | Aimed at management, project leads, and high-level stakeholders involved in decision-making for testing strategies.                               |
| **Contents**             | Includes test scope, objectives, resources, schedule, test environment, test cases, entry/exit criteria, risks, and deliverables. | Covers testing approach, testing types (functional, performance, security, etc.), tools, defect management, risk assessment, and overall process. |
| **Level of Detail**      | Provides a detailed breakdown of test activities, including specific test cases, procedures, and schedules.                       | Offers a broader overview of the testing approach, principles, and guidelines, rather than focusing on specific details.                          |
| **Timeframe**            | Typically created for a specific project phase or release.                                                                        | Generally applies to multiple projects or the entire organization and is less time-bound.                                                         |
| **Flexibility**          | More rigid and specific to the project, allowing less flexibility to adapt to changing circumstances.                             | Offers more flexibility in adapting to various project needs, as it doesn't delve into specifics.                                                 |
| **Dependencies**         | Based on the broader guidelines outlined in the Test Strategy.                                                                    | Driven by the organization's policies, best practices, and project-specific requirements.                                                         |
| **Communication**        | Essential for aligning the project team and stakeholders on the testing approach and execution.                                   | Ensures that testing efforts are aligned with the overall organizational goals and standards.                                                     |
| **Revision and Updates** | Needs to be updated more frequently, especially with changes in project scope or requirements.                                    | Changes less frequently and provides a stable framework for testing efforts across multiple projects.                                             |
| **Example Use Case**     | Creating a detailed plan for testing a specific software release or product update.                                               | Establishing guidelines for how various types of testing (functional, performance, etc.) will be conducted within the organization.               |

---

### Test Coverage Metrics

:memo: ***Functional Coverage***
It defines how much coverage the test plan provides for the business and functional requirements. Function coverage is a metric measuring the functions invoked during software testing. The number of functions executed by a test suite is divided by the total number of functions in the software under testing to calculate this metric. It does not assign a value to each function individually, as branch coverage or statement coverage does. Instead, it simply determines whether each function was called by the tests you were running.

:memo: ***Test Execution Coverage***
It defines what is the percentage of test execution vs the total test case count. It helps understand the amount of test coverage in terms of absolute numbers. This widely helps in understanding the pass or fail rate of the test build.

:memo: ***Requirements Coverage***
It defines how much of the business requirements suggested by the stakeholders are covered in the existing test plan. Requirements coverage can be deciphered by comparing the number of requirements that are fully covered by the test scenarios vs those partially covered or not covered by the test scenarios. 

:memo: ***Product Coverage***
It defines the scope of the test, in terms of the number of products that the product is tested on. For example, a web application that is tested on various desktops, mobiles, and tablets, covers a large number of devices that the application would be accessed on. 

The larger the product coverage, the more it gives confidence for a smoother consistent user experience. Especially, now when the users have access to different types of devices and platforms and companies trying to provide a multi-experience to the users seamlessly across different devices and platforms.

Cross platform compatibility and Cross-Browser Compatibility tests are the biggest examples, where product coverage plays a major role in determining the quality of the software.

:memo: ***Risk Coverage***
It defines the risk faced by the software application when in real use, which is covered by the tests. These risks are mainly the constraints that may cause any negative impact on the user experience. Once the risks are known, testing can be structured to ensure that potential risks are not translated into actual negative consequences. When tests are designed to cover said risks, the software stands a much higher chance of attaining technical and commercial success.

Take an app for stock market investment, for example. Let’s say it uses a third-party API to search and retrieve financial data – exchange rates, stock prices, etc. If this API becomes unresponsive (a major risk), how would the app respond?

Risk coverage would take this into account and design tests accordingly to ensure the software does not become paralyzed and useless if such a risk occurs.

---

### Classification of Different Types of Testing

Testing is divided into two types – *Functional* Testing and *Non functional* Testing

<p align="center" width="100%">
    <img width="100%" src="https://browserstack.wpenginepowered.com/wp-content/uploads/2023/03/Types-of-software-testing-1.png"> 
</p>

---

## pytest

### What is a Pytest fixture?

In testing, a fixture provides a defined, reliable and consistent context for the tests. This could include environment   
(for example a database configured with known parameters) or content (such as a dataset).

```python
import pytest

@pytest.fixture
def sample_data():
    return {"key": "value"}

def test_data(sample_data):
    assert sample_data["key"] == "value"
```

Tests don’t have to be limited to a single fixture, either. They can depend on as many fixtures as you want, and   
fixtures can use other fixtures, as well. This is where pytest’s fixture system really shines.

---

### Explain the `autouse` flag in fixtures.

Automatically applied to all tests in their scope.

```python
@pytest.fixture(autouse=True)
def setup_environment():
    print("Setting up environment")
```
---
### What are pytest's fixture scopes?

You can specify the scope using the scope parameter in the @pytest.fixture decorator.

```python
@pytest.fixture(scope="module")
def example_fixture():
    return "This is an example"
```

|Scope      |	Lifetime|
|-----------|------------------------------------------|
|function   |	Per test function (default).           |
|class      |	Per test class.                        |
|module     |	Per module (file).                     |
|session    |	Per pytest session (entire test suite).|

---

### How do you mark a test in Pytest?

```ini
# pytest.ini
[pytest]
markers =
    slow: marks tests as slow
```
```python
import pytest

@pytest.mark.slow
def test_slow_function():
    assert True
```
```shell
pytest -m "not slow"
```
---

### What is parameterized testing in Pytest?

Parameterized tests allow you to run the same test with different inputs.

```python
import pytest

@pytest.mark.parametrize("a, b, result", [(1, 1, 2), (2, 3, 5), (3, 5, 8)])
def test_addition(a, b, result):
    assert a + b == result
```
---

### How do you handle exceptions in Pytest?

```python
import pytest

def test_exception():
    with pytest.raises(ZeroDivisionError):
        1 / 0
```
---

### How do you run tests in parallel using Pytest?

```shell
pip install pytest-xdist
pytest -n <num_of_cores>
```
---

### What is the purpose of the conftest.py file in Pytest?

`conftest.py` is a configuration file used to share fixtures and hooks across multiple test files.

---

### How do you create custom Pytest hooks, and what are some common hooks?

* Custom hooks allow extending Pytest's behavior.
* Hooks are implemented in `conftest.py` using Pytest’s hook system.

```python
# conftest.py
def pytest_runtest_logreport(report):
    if report.when == "call" and report.outcome == "failed":
        with open("failed_tests.log", "a") as f:
            f.write(f"FAILED: {report.nodeid}\n")
```

**Common hooks**:  
* `pytest_configure(config)`: Called after command-line options are parsed.
* `pytest_collection_modifyitems(config, items)`: Modify collected test items.
* `pytest_runtest_teardown(item)`: Called after each test teardown.

--- 

## References
- https://docs.pytest.org/en/stable/
- https://semaphoreci.com/blog/testing-pyramid
- https://testsigma.com/blog/qa-interview-questions/#
- https://katalon.com/resources-center/blog/test-plan   
- https://www.browserstack.com/guide/types-of-testing
- https://www.browserstack.com/guide/how-to-write-a-bug-report
- https://www.testrail.com/blog/effective-test-cases-templates/
- https://www.browserstack.com/guide/test-coverage-metrics-in-software-testing