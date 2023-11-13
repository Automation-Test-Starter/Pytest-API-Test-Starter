<!-- markdownlint-disable MD041 -->
<!-- markdownlint-disable MD033 -->
<div align="right"><strong>🇨🇳中文</a></strong>  | <strong><a href="./README.md">🇬🇧English</strong></div>
<!-- markdownlint-disable MD041 -->
<!-- markdownlint-disable MD033 -->

# Pytest 接口自动化测试快速启动项目

关于使用 Pytest 进行 API 自动化测试的快速启动项目介绍文档。

- [Pytest 接口自动化测试快速启动项目](#pytest-接口自动化测试快速启动项目)
  - [介绍](#介绍)
    - [Pytest 介绍](#pytest-介绍)
    - [python 虚拟环境介绍](#python-虚拟环境介绍)
  - [项目依赖](#项目依赖)
  - [项目目录结构](#项目目录结构)
  - [从 0 到 1 搭建 Pytest 接口自动化测试项目](#从-0-到-1-搭建-pytest-接口自动化测试项目)
    - [1.创建项目目录](#1创建项目目录)
    - [2.项目初始化](#2项目初始化)
    - [3.安装项目依赖](#3安装项目依赖)
    - [4.新建测试文件及测试用例](#4新建测试文件及测试用例)
    - [5.编写测试用例](#5编写测试用例)
    - [6.运行测试用例](#6运行测试用例)
    - [7.查看测试报告](#7查看测试报告)
    - [8.接入 pytest-html-reporter 测试报告](#8接入-pytest-html-reporter-测试报告)
      - [安装 pytest-html-reporter 依赖](#安装-pytest-html-reporter-依赖)
      - [配置测试报告参数](#配置测试报告参数)
      - [运行测试用例](#运行测试用例)
      - [查看测试报告](#查看测试报告)

## 介绍

### Pytest 介绍

Pytest 是一个流行的 Python 测试框架，用于编写、组织和运行各种类型的自动化测试。它提供了丰富的功能，使您能够轻松编写和管理测试用例，以及生成详细的测试报告。以下是 Pytest 的一些主要特点和优势：

1. **简单和易用**：Pytest 的设计使得编写测试用例变得简单且易于理解。您可以使用 Python 的标准 `assert` 语句来编写测试断言，而不需要学习新的断言语法。

2. **自动发现测试用例**：Pytest 可以自动发现和运行项目中的测试用例，而不需要显式配置测试套件。测试用例文件可以命名为 `test_*.py` 或 `*_test.py`，或使用特定的测试函数命名规范。

3. **丰富的插件生态系统**：Pytest 可以通过插件扩展其功能。有许多第三方插件可用，以满足不同测试需求，如 Allure 报告、参数化、覆盖率分析等。

4. **参数化测试**：Pytest 支持参数化测试，允许您运行相同的测试用例多次，但使用不同的参数。这可以减少代码重复，提高测试覆盖率。

5. **异常和故障定位**：Pytest 提供详细的错误和异常信息，有助于您更容易地定位和解决问题。它还提供详细的回溯（traceback）信息。

6. **并行测试执行**：Pytest 支持并行执行测试用例，提高了测试执行的速度，特别是在大型项目中。

7. **多种报告格式**：Pytest 支持多种测试报告格式，包括终端输出、JUnit XML、HTML 报告和 Allure 报告等。这些报告可以帮助您可视化测试结果。

8. **命令行选项**：Pytest 提供了丰富的命令行选项，以定制测试运行的行为，包括过滤、重试、覆盖率分析等。

9. **集成性**：Pytest 可以与其他测试框架和工具（如 Selenium、Django、Flask 等）以及持续集成系统（如 Jenkins、Travis CI 等）轻松集成。

10. **活跃的社区**：Pytest 拥有一个活跃的社区，有广泛的文档和教程可供学习和参考。您还可以在社区中获得支持和解决问题。

总之，Pytest 是一个强大且灵活的测试框架，适用于各种规模和类型的项目。它的易用性、自动化能力以及丰富的插件使它成为 Python 测试领域的首选工具之一。

官方网站：[https://docs.pytest.org/en/latest/](https://docs.pytest.org/en/latest/)

### python 虚拟环境介绍

Python 虚拟环境（Virtual Environment）是一种机制，用于在单个 Python 安装中创建和管理多个隔离的开发环境。虚拟环境有助于解决不同项目之间的依赖冲突问题，确保每个项目都能够使用其独立的 Python 包和库，而不会相互干扰。以下是如何创建和使用 Python 虚拟环境的步骤：

1. **安装虚拟环境工具**:
   在开始之前，确保您已安装 Python 的虚拟环境工具。在 Python 3.3 及更高版本中，`venv` 模块已经内置，可以使用它来创建虚拟环境。如果您使用较旧版本的 Python，您可以安装 `virtualenv` 工具。

   对于 Python 3.3+，`venv` 工具已内置，无需额外安装。

   对于 Python 2.x，可以使用以下命令安装 `virtualenv` 工具：

   ```bash
   pip install virtualenv
   ```

2. **创建虚拟环境**:
   打开终端，移动到您希望创建虚拟环境的目录，并运行以下命令以创建虚拟环境：

   使用 `venv`（适用于 Python 3.3+）：

   ```bash
   python -m venv myenv
   ```

   使用 `virtualenv`（适用于 Python 2.x）：

   ```bash
   virtualenv myenv
   ```

   在上述命令中，`myenv` 是虚拟环境的名称，您可以自定义名称。

3. **激活虚拟环境**:
   要开始使用虚拟环境，需要激活它。在不同的操作系统中，激活命令略有不同：

   - 在 macOS 和 Linux 上：

     ```bash
     source myenv/bin/activate
     ```

   - 在 Windows 上（使用 Command Prompt）：

     ```bash
     myenv\Scripts\activate
     ```

   - 在 Windows 上（使用 PowerShell）：

     ```bash
     .\myenv\Scripts\Activate.ps1
     ```

   一旦虚拟环境激活，您会在终端提示符前看到虚拟环境的名称，表示您已进入虚拟环境。

4. **在虚拟环境中安装依赖**:
   在虚拟环境中，您可以使用 `pip` 安装项目所需的任何 Python 包和库，这些依赖将与该虚拟环境关联。例如：

   ```bash
   pip install requests
   ```

5. **使用虚拟环境**:
   在虚拟环境中工作时，您可以运行 Python 脚本和使用安装在虚拟环境中的包。这确保了您的项目在独立的环境中运行，不会与全局 Python 安装产生冲突。

6. **退出虚拟环境**:
   要退出虚拟环境，只需在终端中运行以下命令：

   ```bash
   deactivate
   ```

   这将使您返回到全局 Python 环境。

通过使用虚拟环境，您可以在不同项目之间维护干净的依赖关系，并确保项目的稳定性和隔离性。这是 Python 开发中的一个良好实践。

## 项目依赖

> 需提前安装好以下环境

- [x] python, demo 版本为 v3.11.6

> 大家安装 python3.x 以上的版本即可

## 项目目录结构

以下为一个 Pytest 接口自动化测试项目的目录结构示例：

> 后续 demo 项目会引入 allure 报告，所以会多出一个 allure-report 目录

```text
Pytest-allure-demo/
    ├── tests/                  # 存放测试用例文件
    │   ├── test_login.py       # 示例测试用例文件
    │   ├── test_order.py       # 示例测试用例文件
    │   └── ...
    ├── data/                   # 存放测试数据文件（如 JSON、CSV 等）
    │   ├── dev_test_data.json      # 开发环境测试数据文件
    │   ├── prod_test_data.json      # 生产环境测试数据文件
    │   ├── ...
    ├── config/
    │   ├── dev_config.json  # 开发环境配置文件
    │   ├── prod_config.json  # 生产环境配置文件
    │   ├── ...
    ├── conftest.py             # Pytest 的全局配置文件
    ├── pytest.ini              # Pytest 配置文件
    ├── requirements.txt        # 项目依赖项文件
    └── allure-report/          # 存放 Allure 报告
```

## 从 0 到 1 搭建 Pytest 接口自动化测试项目

### 1.创建项目目录

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

### 3.安装项目依赖

```shell
// 安装 requests 包
pip install requests
// 安装pytest 包
pip install pytest
// 将项目依赖项保存到 requirements.txt 文件中
pip freeze > requirements.txt
```

### 4.新建测试文件及测试用例

```shell
// 新建测试文件夹
mkdir tests
// 新建测试用例文件
cd tests
touch test_demo.py
```

### 5.编写测试用例

> 测试接口可参考项目中 demoAPI.md 文件

```python
import requests


class TestPytestDemo:

    def test_get_demo(self):
        base_url = "https://jsonplaceholder.typicode.com"
        # 发起请求
        response = requests.get(f"{base_url}/posts/1")
        # 断言
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
        # 发起请求
        response = requests.post(f"{base_url}/posts", requests_data)
        # 断言
        assert response.status_code == 201
        print(response.json())
        assert response.json()['userId'] == '1'
        assert response.json()['id'] == 101
```

### 6.运行测试用例

```shell
pytest
```

### 7.查看测试报告

![CsoB4y](https://cdn.jsdelivr.net/gh/naodeng/blogimg@master/uPic/CsoB4y.png)

### 8.接入 pytest-html-reporter 测试报告

> <https://github.com/prashanth-sams/pytest-html-reporter>

#### 安装 pytest-html-reporter 依赖

```shell
pip install pytest-html-reporter 
```

#### 配置测试报告参数

- 项目根目录下新建 pytest.ini 文件
- 添加以下内容

```ini
[pytest]
addopts = -vs -rf --html-report=./report --title='PYTEST REPORT' --self-contained-html
```

#### 运行测试用例

```shell
pytest
```

#### 查看测试报告

报告在项目根目录下的 report 目录下，使用浏览器打开 pytest_html_report.html 文件即可查看

![8JdxbA](https://cdn.jsdelivr.net/gh/naodeng/blogimg@master/uPic/8JdxbA.png)
