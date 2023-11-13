<!-- markdownlint-disable MD041 -->
<!-- markdownlint-disable MD033 -->
<div align="right"><strong><a href="./README_ZH.md">🇨🇳中文</a></strong>  | <strong>🇬🇧English</strong></div>
<!-- markdownlint-disable MD041 -->
<!-- markdownlint-disable MD033 -->

# Pytest API Automation Testing QuickStart Project

An introductory QuickStart project document on API automation testing with Pytest.

- [Pytest API Automation Testing QuickStart Project](#pytest-api-automation-testing-quickstart-project)
  - [Introduction](#introduction)
    - [Introducing Pytest](#introducing-pytest)
    - [Introduction to python virtual environments](#introduction-to-python-virtual-environments)
  - [Project dependencies](#project-dependencies)
  - [Project directory structure](#project-directory-structure)
  - [Build a Pytest API Automation Test Project from 0 to 1](#build-a-pytest-api-automation-test-project-from-0-to-1)
    - [1. Create a project directory](#1-create-a-project-directory)
    - [2.项目初始化](#2项目初始化)
    - [3.Install project dependencies](#3install-project-dependencies)
    - [4. Create new test files and test cases](#4-create-new-test-files-and-test-cases)
    - [5. Writing Test Cases](#5-writing-test-cases)
    - [6.Run test cases](#6run-test-cases)
    - [7.View test report](#7view-test-report)
    - [8.Integration pytest-html-reporter test report](#8integration-pytest-html-reporter-test-report)
      - [Install pytest-html-reporter dependency](#install-pytest-html-reporter-dependency)
      - [Configuring Test Report Parameters](#configuring-test-report-parameters)
      - [Run test cases](#run-test-cases)
      - [Viewing the test report](#viewing-the-test-report)

## Introduction

### Introducing Pytest

Pytest is a popular Python testing framework for writing, organizing, and running various types of automated tests. It provides a rich set of features that make it easy to write and manage test cases, as well as generate detailed test reports. Here are some of the key features and benefits of Pytest:

1. **Simple and easy to use**: Pytest is designed to make writing test cases simple and easy to understand. You can write test assertions using Python's standard `assert` statement without having to learn a new assertion syntax.

2. **Automatic Discovery of Test Cases**: Pytest can automatically discover and run test cases in your project without explicitly configuring the test suite. Test case files can be named `test_*.py` or `*_test.py`, or use a specific test function naming convention.

3. **Rich plugin ecosystem**: Pytest can be extended with plugins. There are many third-party plug-ins available to meet different testing needs, such as Allure reporting, parameterization, coverage analysis, and so on.

4. **Parameterized Testing**: Pytest supports parameterized testing, which allows you to run the same test case multiple times, but with different parameters. This reduces code duplication and improves test coverage.

5. **Exception and fault localization**: Pytest provides detailed error and exception information that helps you locate and resolve problems more easily. It also provides detailed traceback information.

6. **Parallel Test Execution**: Pytest supports parallel execution of test cases, which increases the speed of test execution, especially in large projects.

7. **Multiple Report Formats**: Pytest supports multiple test report formats, including terminal output, JUnit XML, HTML reports and Allure reports. These reports can help you visualize test results.

8. **Command Line Options**: Pytest provides a rich set of command line options to customize the behavior of test runs, including filtering, retrying, coverage analysis, and more.

9. **Integration**: Pytest can be easily integrated with other testing frameworks and tools (e.g. Selenium, Django, Flask, etc.) as well as continuous integration systems (e.g. Jenkins, Travis CI, etc.).

10. **Active Community**: Pytest has an active community with extensive documentation and tutorials for learning and reference. You can also get support and solve problems in the community.

In short, Pytest is a powerful and flexible testing framework for projects of all sizes and types. Its ease of use, automation capabilities, and rich set of plugins make it one of the go-to tools in Python testing.

Official website: [https://docs.pytest.org/en/latest/](https://docs.pytest.org/en/latest/)

### Introduction to python virtual environments

A Python virtual environment is a mechanism for creating and managing multiple isolated development environments within a single Python installation. Virtual environments help resolve dependency conflicts between different projects by ensuring that each project can use its own independent Python packages and libraries without interfering with each other. Here are the steps on how to create and use a Python virtual environment:

1. **Install the Virtual Environment Tool**.
   Before you begin, make sure you have installed Python's virtual environment tools. In Python 3.3 and later, the `venv` module is built-in and can be used to create virtual environments. If you're using an older version of Python, you can install the `virtualenv` tool.

   For Python 3.3+, the `venv` tool is built-in and does not require additional installation.

   For Python 2.x, you can install the `virtualenv` tool with the following command:

   ```bash
   pip install virtualenv
   ```

2. **Creating a virtual environment**.
   Open a terminal, move to the directory where you wish to create the virtual environment, and run the following command to create the virtual environment:

   Use `venv` (for Python 3.3+):

   ```bash
   python -m venv myenv
   ```

   Use `virtualenv` (for Python 2.x):

   ```bash
   virtualenv myenv
   ```

   In the above command, `myenv` is the name of the virtual environment and you can customize the name.

3. **Activate virtual environment**.
   To start using the virtual environment, you need to activate it. The activation command is slightly different for different operating systems:

   - on macOS and Linux:

    ```bash
     source myenv/bin/activate
    ```

   - On Windows (using Command Prompt):

    ```bash
     myenv\Scripts\activate
    ```

   - On Windows (using PowerShell):

    ```bash
     .\myenv\Scripts\Activate.ps1
    ```

   Once the virtual environment is activated, you will see the name of the virtual environment in front of the terminal prompt, indicating that you are in the virtual environment.

4. **Installing dependencies in a virtual environment**.
   In a virtual environment, you can use `pip` to install any Python packages and libraries required by your project, and these dependencies will be associated with that virtual environment. Example:

   ```bash
   pip install requests
   ```

5. **Using a virtual environment**.
   When working in a virtual environment, you can run Python scripts and use packages installed in the virtual environment. This ensures that your project runs in a separate environment and does not conflict with the global Python installation.

6. **Exiting the virtual environment**.
   To exit the virtual environment, simply run the following command in a terminal:

   ```bash
   deactivate
   ```

   This returns you to the global Python environment.

By using a virtual environment, you can maintain clean dependencies between projects and ensure project stability and isolation. This is a good practice in Python development.

## Project dependencies

> The following environments need to be installed in advance

- [x] python, demo 版本为 v3.11.6

> Just install python 3.x or higher.

## Project directory structure

The following is an example of the directory structure of a Pytest interface automation test project:

> Subsequent demo projects will introduce allure reports, so there will be an additional allure-report directory.

```text
Pytest-allure-demo/
    ├── tests/                  # test case files
    │   ├── test_login.py       # Example test case file
    │   ├── test_order.py       # Example test case file
    │   └── ...
    ├── data/                   # test data files (e.g. JSON, CSV, etc.)
    │   ├── dev_test_data.json      #  Test data file for development environment.
    │   ├── prod_test_data.json      #  Test data file for prod environment.
    │   ├── ...
    ├── config/
    │   ├── dev_config.json  # Development environment configuration file
    │   ├── prod_config.json  # Production environment configuration file
    │   ├── ...
    ├── conftest.py             # Pytest's global configuration file
    ├── pytest.ini              # Pytest configuration file
    ├── requirements.txt        # Project dependencies file
    └── allure-report/          # Allure reports
```

## Build a Pytest API Automation Test Project from 0 to 1

### 1. Create a project directory

```shell
mkdir Pytest-API-Testing-Demo
```

### 2.项目初始化

```shell
// 进入项目文件夹下
cd Pytest-API-Testing-Demo
// 创建项目 python 项目虚拟环境
python -m venv .env
// 启用项目 python 项目虚拟环境
source .env/bin/activate
```

### 3.Install project dependencies

```shell
// Install the requests package
pip install requests
// Install the pytest package
pip install pytest
// Save the project dependencies to the requirements.txt file.
pip freeze > requirements.txt
```

### 4. Create new test files and test cases

```shell
// Create a new tests folder
mkdir tests
// Create a new test case file
cd tests
touch test_demo.py
```

### 5. Writing Test Cases

> The test API can be referred to the demoAPI.md file in the project.

```python
import requests


class TestPytestDemo:

    def test_get_demo(self):
        base_url = "https://jsonplaceholder.typicode.com"
        # SEND REQUEST
        response = requests.get(f"{base_url}/posts/1")
        # ASSERT
        assert response.status_code == 200
        assert response.json()['userId'] == 1
        assert response.json()['id'] == 1

    def test_post_demo(self):
        base_url = "https://jsonplaceholder.typicode.com"
        requests_data = {
            "title": "foo",
            "body": "bar",
            "userId": 1
        }
        # SEND REQUEST
        response = requests.post(f"{base_url}/posts", requests_data)
        # ASSERT
        assert response.status_code == 201
        print(response.json())
        assert response.json()['userId'] == '1'
        assert response.json()['id'] == 101
```

### 6.Run test cases

```shell
pytest
```

### 7.View test report

![CsoB4y](https://cdn.jsdelivr.net/gh/naodeng/blogimg@master/uPic/CsoB4y.png)

### 8.Integration pytest-html-reporter test report

> <https://github.com/prashanth-sams/pytest-html-reporter>

#### Install pytest-html-reporter dependency

```shell
pip install pytest-html-reporter 
```

#### Configuring Test Report Parameters

- Create a new pytest.ini file in the project root directory.
- Add the following

```ini
[pytest]
addopts = -vs -rf --html-report=./report --title='PYTEST REPORT' --self-contained-html
```

#### Run test cases

```shell
pytest
```

#### Viewing the test report

The report is located in the report directory in the project root directory, use your browser to open the pytest_html_report.html file to view it.

![8JdxbA](https://cdn.jsdelivr.net/gh/naodeng/blogimg@master/uPic/8JdxbA.png)
