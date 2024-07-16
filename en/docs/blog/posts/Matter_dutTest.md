---
date: 2024-07-16
categories:
  - Thread
---


# How to Conduct Matter Test-Harness Certification Testing?

<!-- more -->

## Step 1: Prepare the Environment

1. Install Necessary Software:

- Ensure you have a stable development environment, including Git, Python, Node.js, and Yarn.
- Install Matter SDK: Download and compile the SDK from Matter's official GitHub repository. Use the following commands:

---
    git clone https://github.com/project-chip/connectedhomeip.git
    cd connectedhomeip
    ./scripts/bootstrap.sh
    source scripts/activate.sh
    ./scripts/build_sdk.sh
---

2. Configure Hardware:

Prepare the necessary hardware devices for testing, such as Matter-compatible devices and development boards.


## Step 2: Install Matter Test-Harness

1.Download Matter Test-Harness:

- Download Test-Harness from Matter's GitHub repository.

---
    git clone https://github.com/project-chip/connectedhomeip.git
    cd connectedhomeip/test_harness
---

2.Install Dependencies:

Use Yarn to install the necessary dependencies:

---
    yarn install
---

## Step 3: Configure Test-Harness
1.Edit Configuration File:

Edit the config.json file according to your testing requirements. This file contains parameters and options for testing.

2.Start Matter Test-Harness:

Start Test-Harness to ensure it can discover and communicate with testing devices in your network environment:

---
    yarn start
---

## Step 4: Execute Tests
1.Choose Test Cases:

Test-Harness includes many predefined test cases located in the test_cases directory. Select appropriate test cases and adjust as needed.

2.Run Tests:

Run the selected test case using the following command:

---
    yarn test --test-case <test-case-name>
---

## Step 5: Review Test Results
1.Analyze Test Outputs:

After completing the tests, Test-Harness generates a report including test results and detailed logs.
Locate the test report file in the output directory to review detailed test results and log information.

2.Example Testing Process
Suppose you want to perform a basic connectivity test. Here’s a specific example:

1. Prepare Environment: Install and configure Matter SDK and Test-Harness.
2. Choose Test Case: Select connectivity-test.json from the test_cases directory.
3. Run Test:
---
    yarn test --test-case connectivity-test
---

4. View Test Results: Find connectivity-test-report.json in the output directory to review the test results.

Following these steps, you can conduct basic testing using Matter Test-Harness. For further customization needs, adjust configuration files and test cases according to specific testing goals.