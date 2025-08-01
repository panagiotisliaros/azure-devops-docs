---
title: Requirements traceability
description: Link requirements, tests, and bugs to enable requirements traceability
ms.assetid: 41F15A66-D8C2-43AA-9E38-BCED9A8D3F55
ms.topic: conceptual
ms.author: jeom
author: raviLiftr
ms.date: 07/01/2020
monikerRange: '<= azure-devops'
ms.custom:
  - continuous-test
  - cross-service
  - sfi-image-nochange
---

# Requirements traceability

[!INCLUDE [version-lt-eq-azure-devops](../../includes/version-lt-eq-azure-devops.md)]

**Requirements traceability** is the ability to relate and document two or more phases of 
a development process, which can then be traced both forward or backward from its origin.
Requirements traceability helps teams to get insights into indicators such as
**quality of requirements** or **readiness to ship the requirement**.
A fundamental aspect of requirements traceability is association of the requirements to test cases, bugs, and code changes.

Read the [glossary](./test-glossary.md) to understand test report terminology.

<a name="agileteams"></a>

## Agile teams running automated tests 

Agile teams have characteristics including, but not limited to the following 

* Faster release cycles 
* Continuous testing in a pipeline
* Negligible manual testing footprint; limited to exploratory testing
* High degree of automation

The following sections explore traceability from **Quality**, **Bug**, and **Source** standpoints for Agile teams.

<a name="qualitytraceability"></a>

### Quality traceability

:::moniker range="<=azure-devops"

Link project requirements to test results for end-to-end traceability with a simple way to monitor test results. To link automated tests with requirements, see [Test report](review-continuous-test-results-after-build.md).

1. In the results section under **Tests** tab of a build or release summary,
   select the test to be linked to requirements and choose **Link**. 

   ![Select tests to be linked to requirements](media/requirements-traceability/link-results-to-requirements.png)

2. Choose a work item to be linked to the selected test in one of the following ways:

   * Choose an applicable work item from the list of suggested work items. The list is based on the most recently viewed and updated work items.
   * Specify a work item ID.
   * Search for a work item based on the title text.

   ![Select requirements work item](media/requirements-traceability/select-workitem.png)

   > The list shows only work items belonging to the Requirements category. 

3. Teams often want to pin the summarized view of requirements traceability to a dashboard.
   Use the [Requirements quality](../../report/dashboards/widget-catalog.md) widget to do so.

   ![Create team dashboard](media/requirements-traceability/team-dashboard.png)

4. Configure the **Requirements quality** widget with the required options and save it.

   * **Requirements query**: Select a work item query that captures the requirements, such as the user stories in the current iteration.
   * **Quality data**: Specify the stage of the pipeline for which the requirements quality should be traced.

   ![Configure widget](media/requirements-traceability/configure-widget.png)

5. View the widget in the team's dashboard. It lists all the **Requirements** in scope,
   along with the **Pass Rate** for the tests and count of Failed tests. Selecting a **Failed** test
   count opens the **Tests** tab for the selected build or release.
   The widget also helps to track the requirements without any associated test.

   ![Track requirements without tests](media/requirements-traceability/requirements-quality-widget.png)

:::moniker-end

<a name="bugtraceability"></a>

### Bug traceability

Testing gives a measure of the confidence to ship a change to users. A test failure signals an issue with the change. Failures can occur due to errors in the source under test, bad test code, environmental issues, [flaky tests](test-glossary.md), and more.
Bugs provide a robust way to track test failures and drive accountability in the team to take the required remedial actions.
To associate bugs with test results, see [Test report](review-continuous-test-results-after-build.md).

1. In the results section of the Tests tab, select the tests against which the bug should be created and choose **Bug**. Multiple test results can be mapped to a single bug, which is typically done when the reason for the failures attributes to a single cause, such as an unavailable dependent service, a database connection failure, or similar issues.

   ![Link bugs to tests](media/requirements-traceability/link-bugs-to-tests.png)

2. Open the work item. The bug captures the complete context of the test results including key information, such as the error message, stack trace, comments, and more.

   ![Capture bug details](media/requirements-traceability/capture-bug-details.png)

3. View the bug with the test result, directly in context, within the **Tests** tab.
   The **Work Items** tab also lists any linked requirements for the test result.

   ![View bug in Tests Tab](media/requirements-traceability/view-bug-in-tests-tab.png)

4. From a work item, navigate directly to the associated test results.
   Both the [test case](test-glossary.md) and the specific [test result](test-glossary.md) are linked to the bug.

   ![Test links in bug](media/requirements-traceability/test-link-in-bug.png)

5. In the work item, select **Test case** or **Test result** to go directly to the **Tests** page
   for the selected build or release. You can troubleshoot the failure, update your analysis
   in the bug, and make the changes required to fix the issue as applicable.
   While both the links take you to the **Tests tab**, the default sections include **History** and **Debug**.

   ![Tests Tab full page view](media/requirements-traceability/redirect-to-tests-tab.png)

<a name="sourcetraceability"></a>

### Source traceability

When troubleshooting test failures that occur consistently over a period of time,
it's important to trace back to the initial set of changes - where the failure originated.
This step can help significantly to narrow down the scope for identifying the problematic test or
source under test. To discover the first instance of test failures and trace it back to the associated code changes,
visit [Tests tab](review-continuous-test-results-after-build.md) in build or release.

1. In the **Tests** tab, select a test failure to be analyzed.
   Based on whether it's a build or release, choose the **Failing build** or **Failing release** column for the test. 

   ![View Failing release](media/requirements-traceability/view-failing-release.png)

   Another instance of the **Tests** tab opens in a new window, showing the first instance of consecutive failures for the test.

   ![originating test failure](media/requirements-traceability/view-originating-test.png)

2. Based on the build or release pipeline, you can choose the timeline or pipeline view to see what code changes were committed.
   You can analyze the code changes to identify the potential root cause of the test failure.

   ![View code commits](media/requirements-traceability/view-code-commits.png)

<a name="traditionalteams"></a>

## Traditional teams using planned testing

Teams moving from manual testing to continuous, automated testing, and have a subset of tests that are already automated, can [execute them as part of the pipeline or on demand](review-continuous-test-results-after-build.md).
**Planned testing**, or "automated tests" can be [associated to the test cases](../../test/associate-automated-test-with-test-case.md)
in a test plan and executed from **Azure Test Plans**.
Once associated, these tests contribute towards the quality metrics of the corresponding requirements.

[!INCLUDE [help-and-support-footer](includes/help-and-support-footer.md)] 
