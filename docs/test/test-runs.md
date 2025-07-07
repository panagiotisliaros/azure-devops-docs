
# What is a test run?
-------------------

A test run is a container that captures the execution of one or more test cases in Azure DevOps. It represents a specific instance of test execution and is used to track the outcome, duration, and related details of the test cases execution. Test runs are typically created when test cases are executed from a test plan.

Test runs help teams:
*   Monitor test progress and quality trends.
*   Identify regressions or failures quickly.
*   Audit and analyze historical test data.

Once clicking on the "Runs" menu option of Test Plans:

![image.png](/.attachments/image-aa7aa10b-8aca-4419-8778-5b22829660d2.png)
_Run option on the Test Plans side Menu_

The test runs page will load:
![image.png](/.attachments/image-c7032226-8289-4595-becc-cfdd2158ffdf.png)
_Test runs landing page_

Users can browse all the test runs available to them. To make it easier finding the run that they are looking, users can search runs based on their ID as well other attributes of them via the top search bar. 

![image.png](/.attachments/image-66ba8461-2fae-4f97-adfc-d73c20e13a17.png)
_Search bar_

Additionally to make it easier for end users to browse and read through the available runs, the columns of the test run page are configurable with the users being able to choose with of the available columns they like to see. 

So once clicking on the "Column options" on the top right of the screen:

![image.png](/.attachments/image-840c993f-fd51-4203-a56b-a0ab233fac27.png)

the users can configure their self view of the test runs:

![image.png](/.attachments/image-f932d9c6-c71e-4010-95e1-40d88634e61b.png)

# Core elements of a test run

When a run is selected, then a new screen will load with more details on the specific run. 

Core elements of this page are:

## Run states

Depending on the combination of the test cases' results that compose a run, the run itself can have one of the three following states: "Completed", "Needs investigation", or "In progress".

In more detail: 

| **Run State**         | **Test Case Results**                  | **Description**                                                                  |
|-----------------------|----------------------------------------|----------------------------------------------------------------------------------|
| Completed             | All test cases Passed.                  | The test run has finished, and all tests passed.                                |
| Completed             | One or more test cases Not Executed, rest Passed. | The run is marked complete, with some tests were skipped or not run.  |
| Needs investigation   | One or more test cases Failed.          | The test run has finished, and some tests failed.                               |
| Needs investigation   | One or more test cases Blocked.         | The test run has finished, and some tests are marked as blocked.                |
| In progress           | One or more test cases are Paused.      | The run is currently paused and can be resumed later.                           |


## Run summary
This is the main page of each run. It gives to the users information on: 
*   **Pass rate**: Percentage of ran cases that Passed. Note that cases marked during the run as "Not applicable", do not count against the Pass rate calculation. 
*   **Comment**: Comments related to the run can be added. Note that these are comments separate from the comments left during the execution of the tests.  
*   **Test case results**: The outcome (i.e. Passed, Failed, Not Executed) of each scoped test case.
*   **Test run metadata**: Information about who ran the test, when it was run, and on which environment.
*   **Attachments and logs**: Screenshots, logs, or other artifacts collected during execution.


![image.png](/.attachments/image-5e3489ea-0cc6-4360-9569-631c984387ac.png)
_You can view and manage test runs from the **Runs** tab in the **Test Plans** hub or programmatically via the Azure DevOps [REST API](https://learn.microsoft.com/en-us/rest/api/azure/devops/test/runs?view=azure-devops-rest-7.1)._


## Analytics

Each test run comes with a predefined analytics dashboard breaking down the run test cases per their outcome, priority, configuration, failure type, and resolution. 
![image.png](/.attachments/image-9cd3eb65-9326-4980-a00c-5560b2218e4f.png)

The subcategories of each dashboard tile can be filtered out so to provide the focused insights needed as per the needs of each end user. Filtering is possible by clicking on each of the subcategories text.

For example: 

![image.png](/.attachments/image-388400f5-58b2-4fae-bed2-34301c670c4e.png)

In the above scenario, the user has selected to filter out the blocked outcomes, so to only keep the count of failed ones. Note that in the center of the tile the sum of ran cases still shows, while on the colored circle the count of failed cases is seen.

## Attachments

For each of runs the user has the option to attach any related files to support the specific test run. 

Attachment of files is possible by clicking on the "+ Add" button. 

![image.png](/.attachments/image-4db8409f-3585-4e5d-9304-cb501ff32f4e.png)

Once one or more files are attached users can Download or Delete them. Plus add more attachments as needed. 


![image.png](/.attachments/image-904fcd1d-c586-4dca-ba3c-aad6eb6a26f4.png)
_Note that that for specific filetypes e.g. images, on click on the file name, their instant preview is possible._

## Test case results

Lower in the run page's run summary tab, the test case results are available to be reviewed and further analyzed. 

In a similar way that the main run page can be configured for which columns to show, the test case results have the same capability and users can choose for themselves what information they like to have presented. 

![image.png](/.attachments/image-43123007-6ea0-4578-82e7-521d1724e39f.png)
_Test case results_

In this part of the page its possible to as well link the ran cases with other Azure DevOps items as well as bugs. Regarding bug relation to the case(s), either a new bug can be created or an existing bug can be reused. 

To do so, you can select from the checkmarks the cases that you like to relate to Azure DevOps items or bugs and then click on the needed action. 

![image.png](/.attachments/image-65277583-db2f-47db-9cf5-0ea35d189228.png)
_Marked case for further item relation_


# Detailed test case results

To further see the detailed results of a ran case, users can click on the respective case that they are interested in and a new screen will load. 

![image.png](/.attachments/image-da871b99-5a07-4d23-919a-811c233b8466.png)
_Detailed test case results_

In the detailed test case result page are presented: 

- the summary of the case
- the linked work items, including bugs  
- the detailed steps of the case with their outcomes and comments 
- and for failed, paused and blocked cases only, the case analysis information. 

## Analysis information

For failed, paused and blocked cases only, the case analysis is available for being filled in post-run.

This information structures the analysis of the specific case's non-passed outcome towards the path to green. 

![image.png](/.attachments/image-5a1667b5-3ff8-42f1-b189-a30bb9273326.png)


# Related articles 
TBD
