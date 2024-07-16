---
date: 2024-07-16
categories:
  - Thread
---

# Matter Test-Harness 认证测试要如何进行？

<!-- more -->

## 步骤一：准备环境

1.安装必要的软件：


- 确保你有一个稳定的开发环境，包括 Git、Python、Node.js 和 Yarn 等。
- 安装 Matter SDK：从 Matter 的官方 GitHub 仓库下载并编译 SDK。你可以使用以下命令：

---
    git clone https://github.com/project-chip/connectedhomeip.git
    cd connectedhomeip
    ./scripts/bootstrap.sh
    source scripts/activate.sh
    ./scripts/build_sdk.sh
---


2.配置硬件：

- 准备测试所需的硬件设备，如 Matter 兼容设备、开发板等。

## 步骤二：安装 Matter Test-Harness

1.下载 Matter Test-Harness：


从 Matter 的 GitHub 仓库下载 Test-Harness。

---
    git clone https://github.com/project-chip/connectedhomeip.git
    cd connectedhomeip/test_harness
---


2.安装依赖：

使用 Yarn 安装必要的依赖：

---
    yarn install
---

## 步骤三：配置 Test-Harness

1.编辑配置文件：

- 根据你的测试需求编辑 config.json 文件。这个文件包含了测试的参数和选项。

2.启动 Matter Test-Harness：


启动 Test-Harness，确保它在你的网络环境中能够发现和与测试设备进行通信：

---
    yarn start
---

## 步骤四：执行测试

1.选择测试用例：


- Test-Harness 包含了许多预定义的测试用例。你可以在 test_cases 目录中找到这些用例。
- 选择合适的测试用例，根据需要进行调整。


2.运行测试：


通过以下命令运行选定的测试用例：

---
    yarn test --test-case &lt;test-case-name&gt;
---

## 步骤五：查看测试结果

1.分析测试输出：


- 测试完成后，Test-Harness 会生成一个报告，包含测试结果s和详细的日志。
- 在 output 目录中查找测试报告文件，查看测试的详细结果和日志信息。

2.示例测试过程

假设你要运行一个基本的连接性测试，以下是一个具体的例子：

1. 准备环境：安装并配置 Matter SDK 和 Test-Harness。
2. 选择测试用例：在 test_cases 目录中选择 connectivity-test.json。
3. 运行测试：

---
     yarn test --test-case connectivity-test
---

4. 查看测试结果：在 output 目录中找到 connectivity-test-report.json，查看测试结果。

通过以上步骤，你可以使用 Matter Test-Harness 进行基本的测试。如果有进一步的定制需求，你可以根据具体的测试目标调整配置文件和测试用例。