# Public Documentation for the New Test Runs Feature

## !This feature is in public preview and can be changed at any time!

Microsoft’s Azure DevOps team has a new experience in place for the Azure Test Plans’ Run pages.

The experience is automatically activated in your org and you still have the option to disable it.

In case you decide to deactivate the experience and use the old one, you
can follow the two steps seen below. I.e. click on the preview features
menu, find the “New Test Run Hub” and then deactivate it. Note that you
will be asked as well for your feedback on why you decided to turn the
feature off; please consider leaving your feedback, as it's been
actively reviewed by the Azure DevOps product team.

<img src="media/image1.png" style="width:6.5in;height:3.75in" />

## What is a test run?

A test run is a container that captures the execution of one or more
test cases in Azure DevOps. It represents a specific instance of test
execution and is used to track the outcome, duration, and related
details of the test cases' execution. Test runs are typically created
when test cases are executed from a test plan or a pipeline.

Test runs help teams:

- Monitor test progress and quality trends.

- Identify regressions or failures quickly.

- Audit and analyze historical test data.

Once clicking on the "Runs" menu option of Test Plans:

<img src="media/image2.png" style="width:2.78125in;height:2.60417in" />  
*Run option on the Test Plans side Menu*

The test runs page will load:

<img src="media/image3.png" style="width:6.5in;height:3.09375in" />*Test
runs landing page*

Users can browse all the test runs available to them. To make it easier
to find the run that they are looking for, users can search runs based
on the test run ID or other attributes found in the dropdown filters via
the top search bar.

Note:

- The default filters for every time the run page loads are set to runs
  of the last 7 days (“Past 7d”) and “Manual” runs. Similar to when the
  filters are cleared.

- When searching based on test run ID a partial match of the ID is
  possible.

- All search filters are additive to each other. For example, if the
  timeline of the test runs is filtered to the ones that were run in the
  last 7 days; then when searching for a run older than that no results
  will come, and the user shall expand the filter to a longer timeframe.

<img src="media/image4.png" style="width:6.5in;height:0.44792in" />*Search
bar*

Further on, to make it easier for end users to browse and read through
the runs, the columns of the test run page are configurable, with users
being able to choose which of the available columns they would like to
see.

So once clicking on the "Column options" on the top right of the screen:

<img src="media/image5.png" style="width:6.5in;height:1.60417in" />

Users can configure their own view of the test runs:

<img src="media/image6.png" style="width:3.13218in;height:4.18519in" />

Note that the Pipeline Run and Pipeline Run Tested column options are
relevant to automated runs only.

### Core elements of a test run

When a run is selected, a new screen will load with more details on the
specific run.

Core elements of this page are:

#### Run states

Depending on the combination of the test cases' results that compose a
run, the run itself can have one of the three following states:
"Completed", "Needs investigation", or "In progress".

In more detail:

| **Manual Run State** | **Manual Test Case Results** | **Description** |
|----|----|----|
| Completed | All test cases Passed. | The test run has finished, and all tests passed. |
| Completed | One or more test cases Excluded (i.e. set as not applicable), rest Passed. | The run is marked complete, with some tests skipped or not run. |
| Needs investigation | One or more test cases Failed. | The test run has finished, and some tests failed. |
| Needs investigation | One or more test cases Blocked. | The test run has finished, and some tests are marked as blocked. |
| In progress | One or more test cases are Paused. | The run is currently paused and can be resumed later. |

#### Run summary

This is the main page of each run. It provides information on:

- **Pass rate**: Percentage of ran cases that Passed. Note that cases
  marked during the run as "Not applicable", do not count against the
  Pass rate calculation.

- **Comment**: Comments related to the run can be added. These are
  comments distinct from the comments left during the execution of the
  tests. Markdown language is support as well in this field.

- **Test case results**: The outcome (i.e. Passed, Failed, Not Executed)
  of each scoped test case.

- **Test run metadata**: Information about who ran the test, when it was
  run, and on which environment.

- **Attachments and logs**: Screenshots, logs, or other artifacts
  collected during execution.

<img src="media/image7.png" style="width:6.5in;height:2.78125in" />*Run
main view*

Users can view and manage test runs from the **Runs** tab in the **Test
Plans** hub or programmatically via the Azure DevOps [REST
API](https://learn.microsoft.com/en-us/rest/api/azure/devops/test/runs?view=azure-devops-rest-7.1)
.

#### Attachments

For each run, the user has the option to attach any related files to
support the specific test run.

Attachment of files is possible by clicking on the "+ Add" button.

<img src="media/image8.png" style="width:6.5in;height:2.46875in" />*Adding
attachments to the run*

Once one or more files are attached, users can Download or Delete them,
or further add more attachments as needed.

<img src="media/image9.png" style="width:6.5in;height:2.78125in" />*Run
attachments list*

Note that for specific file types, e.g., images and .pdf, clicking on
the file name allows for instant preview.

Additionally note that any attachments added to the run are only related
to the level of the run and not of the individual test results under it.

For attachments on the test result level of the run, the dedicated
attachment tabs can be used. As well any attachment added during each
cases’ run can be found on the level of the test results too.

#### Analytics

Each test run comes with a predefined analytics dashboard breaking down
the test results by their outcome, priority, configuration, failure
type, and resolution.

<img src="media/image10.png" style="width:5.23457in;height:3.43099in"
alt="A screenshot of a computer AI-generated content may be incorrect." />

*Run analytics*

The subcategories of each dashboard tile can be filtered out to provide
the focused insights needed for each end user. Filtering is possible by
clicking on each of the subcategory texts.

For example:

<img src="media/image11.png" style="width:2.05525in;height:2.07292in"
alt="A screenshot of a graph AI-generated content may be incorrect." />

*Subcategory tile filtering*

In the above scenario, the user has selected to filter out the blocked
outcomes, so only the count of failed ones is kept. Note that in the
center of the tile the sum of run cases still shows, while on the
colored circle the count of failed cases is seen.

#### Test case results

Lower in the run page's run summary tab, the test case results are
available to be reviewed and further analyzed.

In a similar way that the main run page can be configured for which
columns to show, the test case results have the same capability, and
users can choose for themselves what information they would like to have
presented.

<img src="media/image12.png" style="width:6.5in;height:2.94792in" />*Test
case results*

In this part of the page, it is possible to also link the test results
with other Azure DevOps work items, e.g. bugs. Regarding bug relation to
the case(s), either a new bug can be created, or an existing bug can be
reused.

To do so, you can select from the checkmarks the cases that you like to
relate to Azure DevOps items or bugs and then click on the needed
action.

<img src="media/image13.png" style="width:3.42188in;height:2.34743in" />  
*Marked case for item relation*

### Detailed test case results

To further study the detailed test result, users can click on the
respective case that they are interested in, and a new screen will load.

<img src="media/image14.png" style="width:5.97133in;height:4.36366in" />  
*Detailed test case results*

In the detailed test case result page are available:

- the summary of the test result,

- the linked work items, including bugs,

- the detailed steps of the case with their outcomes and comments,

- the case analysis information,

- attachments tab, with all attachments from the test result.

### Analysis information

The case analysis is available for being filled in post-run. This
information structures the analysis of the specific case's outcome
towards needed next actions.

Note that for failed, paused and blocked cases, there are few additional
triaging dedicated
[fields](https://learn.microsoft.com/en-us/azure/devops/test/manage-test-failure-type)
compared to the cases with passed status.

Additionally, the comment field is dedicated to the analysis itself, and
once more separate from other comment fields found e.g. on the run or
test results.

<img src="media/image15.png" style="width:3.40101in;height:2.69792in" />

## Related articles

TBD..
