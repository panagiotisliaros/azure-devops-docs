---
title: Configure schedules to run pipelines
description: Configure schedules to run pipelines
ms.topic: conceptual
ms.collection: ce-skilling-ai-copilot
ms.custom: copilot-scenario-highlight
ms.author: sdanie
author: steved0x
ms.date: 02/27/2025
ms.update-cycle: 180-days
monikerRange: '<= azure-devops'
---

# Configure schedules for pipelines

[!INCLUDE [version-lt-eq-azure-devops](../../includes/version-lt-eq-azure-devops.md)]

Azure Pipelines provides several types of triggers to configure how your pipeline starts.

* Scheduled triggers start your pipeline based on a schedule, such as a nightly build. This article provides guidance on using scheduled triggers to run your pipelines based on a schedule.
* Event-based triggers start your pipeline in response to events, such as creating a pull request or pushing to a branch. For information on using event-based triggers, see [Triggers in Azure Pipelines](../build/triggers.md).

You can combine scheduled and event-based triggers in your pipelines, for example to validate the build every time a push is made ([CI trigger](../build/triggers.md#ci-triggers)), when a pull request is made ([PR trigger](../build/triggers.md#pr-triggers)), and a nightly build (Scheduled trigger). If you want to build your pipeline only on a schedule, and not in response to event-based triggers, ensure that your pipeline doesn't have any other triggers enabled. For example, YAML pipelines in a GitHub repository have CI triggers and PR triggers enabled by default. For information on disabling default triggers, see [Triggers in Azure Pipelines](../build/triggers.md) and navigate to the section that covers your repository type.

## Scheduled triggers

#### [YAML](#tab/yaml/)

::: moniker range="<=azure-devops"

> [!IMPORTANT]
> Scheduled triggers defined using the pipeline settings UI take precedence over YAML scheduled triggers.
> 
> If your YAML pipeline has both YAML scheduled triggers and UI defined scheduled triggers, 
> only the UI defined scheduled triggers are run. 
> To run the YAML defined scheduled triggers in your YAML pipeline,
> you must remove the scheduled triggers defined in the pipeline settings UI.
> Once all UI scheduled triggers are removed, a push must be made in order for the YAML 
> scheduled triggers to start being evaluated.
>
> To delete UI scheduled triggers from a YAML pipeline, see [UI settings override YAML scheduled triggers](../troubleshooting/troubleshoot-triggers.md#ui-settings-override-yaml-scheduled-triggers).

Scheduled triggers configure a pipeline to run on a schedule defined using [cron syntax](#cron-syntax).

::: moniker-end

::: moniker range="<azure-devops-2022"

```yaml
schedules:
- cron: string # cron syntax defining a schedule
  displayName: string # friendly name given to a specific schedule
  branches:
    include: [ string ] # which branches the schedule applies to
    exclude: [ string ] # which branches to exclude from the schedule
  always: boolean # whether to always run the pipeline or only if there have been source code or pipeline settings changes since the last successful scheduled run. The default is false.
```

::: moniker-end

::: moniker range="> azure-devops-2022"

```yaml
schedules:
- cron: string # cron syntax defining a schedule
  displayName: string # friendly name given to a specific schedule
  branches:
    include: [ string ] # which branches the schedule applies to
    exclude: [ string ] # which branches to exclude from the schedule
  always: boolean # whether to always run the pipeline or only if there have been source code or pipeline settings changes since the last successful scheduled run. The default is false.
  batch: boolean # Whether to run the pipeline if the previously scheduled run is in-progress; the default is false.
  # batch is available in Azure DevOps Server 2022.1 and higher
```

::: moniker-end

::: moniker range="<=azure-devops"

Scheduled pipelines in YAML have the following constraints.

- The time zone for cron schedules is UTC. [You can get AI assistance from GitHub Copilot to create your cron expressions](#use-github-copilot-to-create-a-cron-expression).
- If you specify an `exclude` clause without an `include` clause for `branches`, it's equivalent to specifying `*` in the `include` clause.
- You can't use pipeline variables when specifying schedules.
- If you use [templates in your YAML file](templates.md), then the schedules must be specified in the main YAML file and not in the template files.

### Branch considerations for scheduled triggers

Scheduled triggers are evaluated for a branch when the following events occur.

* A pipeline is created.
* A pipeline's YAML file is updated, either from a push, or by editing it in the pipeline editor.
* A pipeline's YAML file path is [updated to reference a different YAML file](../customize-pipeline.md#pipeline-settings). This change only updates the default branch, and therefore only picks up schedules in the updated YAML file for the default branch. If any other branches subsequently merge the default branch, for example `git pull origin main`, the scheduled triggers from the newly referenced YAML file are evaluated for that branch.
* A new branch is created. 

After one of these events occurs in a branch, any scheduled runs for that branch are added, if that branch matches the branch filters for the scheduled triggers contained in the YAML file in that branch.

> [!IMPORTANT]
> Scheduled runs for a branch are added only if the branch matches the branch filters for the 
> scheduled triggers in the YAML file **in that particular branch**.

For example, a pipeline is created with the following schedule, and this version of the YAML file is checked into the `main` branch. This schedule builds the `main` branch on a daily basis.

```yaml
# YAML file in the main branch
schedules:
- cron: '0 0 * * *'
  displayName: Daily midnight build
  branches:
    include:
    - main
```

Next, a new branch is created based off of `main`, named `new-feature`. The scheduled triggers from the YAML file in the new branch are read, and since there's no match for the `new-feature` branch, no changes are made to the scheduled builds, and the `new-feature` branch isn't built using a scheduled trigger.

If `new-feature` is added to the `branches` list and this change is pushed to the `new-feature` branch, the YAML file is read, and since `new-feature` is now in the branches list, a scheduled build is added for the `new-feature` branch.

```yaml
# YAML file in the new-feature-branch
schedules:
- cron: '0 0 * * *'
  displayName: Daily midnight build
  branches:
    include:
    - main
    - new-feature
```

Now consider that a branch named `release` is created based off `main`, and then `release` is added to the branch filters in the YAML file in the `main` branch, but not in the newly created `release` branch.

```yaml
# YAML file in the release branch
schedules:
- cron: '0 0 * * *'
  displayName: Daily midnight build
  branches:
    include:
    - main

# YAML file in the main branch with release added to the branches list
schedules:
- cron: '0 0 * * *'
  displayName: Daily midnight build
  branches:
    include:
    - main
    - release
```

Because `release` was added to the branch filters in the `main` branch, but **not** to the branch filters in the `release` branch, the `release` branch won't be built on that schedule. Only when the `release` branch is added to the branch filters in the YAML file **in the release branch** will the scheduled build be added to the scheduler.

::: moniker-end

::: moniker range=">=azure-devops-2022"

### Batch considerations for scheduled triggers

::: moniker-end

::: moniker range="=azure-devops-2022"

> [!NOTE]
> The `batch` property is available on Azure DevOps Server 2022.1 and higher.

::: moniker-end

::: moniker range=">=azure-devops-2022"

The `batch` property configures whether to run the pipeline if the previously scheduled run is in-progress. When `batch` is `true`, a new pipeline run won't start due to the schedule if a previous pipeline run is still in-progress. The default is `false`.

The `batch` property is affected by the setting of the `always` property. When `always` is `true`, the pipeline runs according to the cron schedule, even when `batch` is `true` and there is an in-progress run.

| Always | Batch | Behavior |
|--------|-------|----------|
| `false` | `false` | Pipeline runs only if there's a change with respect to the last successful scheduled pipeline run, even if there's an in-progress run from the last scheduled trigger. |
| `false` | `true` | Pipeline runs only if there's a change with respect to the last successful scheduled pipeline run, and there's no in-progress scheduled pipeline run. |
| `true` | `false` | Pipeline runs according to the cron schedule. |
| `true` | `true` | Pipeline runs according to the cron schedule even if there is an in-progress run. |

### Build.CronSchedule.DisplayName variable

::: moniker-end

::: moniker range="=azure-devops-2022"

> [!NOTE]
> The `Build.CronSchedule.DisplayName` variable is available on Azure DevOps Server 2022.1 and higher.

::: moniker-end

::: moniker range=">=azure-devops-2022"

When a pipeline is running due to a cron scheduled trigger, the pre-defined `Build.CronSchedule.DisplayName` variable contains the `displayName` of the cron schedule that triggered the pipeline run.

Your YAML pipeline may contain multiple cron schedules, and you may want your pipeline to run different stages or jobs based on which cron schedule runs. For example, you have a nightly build and a weekly build, and you want to run a certain stage only during the nightly build. You can use the `Build.CronSchedule.DisplayName` variable in a job or stage condition to determine whether to run that job or stage.

```yml
- stage: stage1
  # Run this stage only when the pipeline is triggered by the 
  # "Daily midnight build" cron schedule
  condition: eq(variables['Build.CronSchedule.DisplayName'], 'Daily midnight build')
```

For more examples, see [schedules.cron examples](/azure/devops/pipelines/yaml-schema/schedules-cron#examples).

::: moniker-end

#### [Classic](#tab/classic/)

Select the days and times when you want to run the build using the classic editor.

If your repository is Azure Repos Git, GitHub, or Other Git, then you can also specify branches to include and exclude. If you want to use wildcard characters, then type the branch specification (for example, `features/modules/*`) and then press Enter.

::: moniker range="<=azure-devops"

![Scheduled trigger UTC + 5:30 time zone](media/triggers/scheduled-trigger-git-india.png)

::: moniker-end

* * *

## Examples

#### [YAML](#tab/yaml/)

::: moniker range="<=azure-devops"

The following example defines two schedules: 

```yaml
schedules:
- cron: '0 0 * * *'
  displayName: Daily midnight build
  branches:
    include:
    - main
    - releases/*
    exclude:
    - releases/ancient/*
- cron: '0 12 * * 0'
  displayName: Weekly Sunday build
  branches:
    include:
    - releases/*
  always: true
```

The first schedule, **Daily midnight build**, runs a pipeline at midnight every day, but only if the code has changed since the last successful scheduled run, for `main` and all `releases/*` branches, except the branches under `releases/ancient/*`.

The second schedule, **Weekly Sunday build**, runs a pipeline at noon on Sundays, whether the code has changed or not since the last run, for all `releases/*` branches.

> [!NOTE]
> The time zone for cron schedules is UTC, so in these examples, the midnight build and the noon build are at midnight and noon in UTC.

For more examples, see [Migrating from the classic editor](#migrating-from-the-classic-editor).

::: moniker-end

#### [Classic](#tab/classic/)

#### Example: Nightly build of Git repo in multiple time zones

::: moniker range="<=azure-devops"

In this example, the classic editor scheduled trigger has two entries, which produce the following builds.

* Every Monday - Friday at 3:00 AM (UTC + 5:30 time zone), build branches that meet the `features/india/*` branch filter criteria

    ![Scheduled trigger UTC + 5:30 time zone](media/triggers/scheduled-trigger-git-india.png)

* Every Monday - Friday at 3:00 AM (UTC - 5:00 time zone), build branches that meet the `features/nc/*` branch filter criteria

    ![Scheduled trigger UTC -5:00 time zone](media/triggers/scheduled-trigger-git-nc.png)

::: moniker-end

#### Example: Nightly build with different frequencies

::: moniker range="<=azure-devops"

**Azure Pipelines and Azure DevOps 2019 Server**

In this example, the classic editor scheduled trigger has two entries, producing the following builds.

* Every Monday - Friday at 3:00 AM UTC, build branches that meet the `main` and `releases/*` branch filter criteria

    ![Scheduled trigger frequency 1, Azure Pipelines and Azure DevOps 2019 Server.](media/triggers/scheduled-trigger-git-week-day-night.png)

* Every Sunday at 3:00 AM UTC, build the `releases/lastversion` branch, even if the source or pipeline hasn't changed

    ![Scheduled trigger frequency 2, Azure Pipelines and Azure DevOps 2019 Server.](media/triggers/scheduled-trigger-git-weekly-night.png)

::: moniker-end

* * *

## Cron syntax

#### [YAML](#tab/yaml/)

::: moniker range="<=azure-devops"

Each Azure Pipelines scheduled trigger cron expression is a space-delimited expression with five entries in the following order. The expression is enclosed in single quotes `'`.

```
mm HH DD MM DW
 \  \  \  \  \__ Days of week
  \  \  \  \____ Months
   \  \  \______ Days
    \  \________ Hours
     \__________ Minutes
```

Field        | Accepted values
-------------|----------------
Minutes      | 0 through 59
Hours        | 0 through 23
Days         | 1 through 31
Months       | 1 through 12, full English names, first three letters of English names
Days of week | 0 through 6 (starting with Sunday), full English names, first three letters of English names

Values can be in the following formats.

Format          | Example          | Description
----------------|------------------|------------
Wildcard        | `*`              | Matches all values for this field
Single value    | `5`              | Specifies a single value for this field
Comma delimited | `3,5,6`          | Specifies multiple values for this field. Multiple formats can be combined, like `1,3-6`
Ranges          | `1-3`            | The inclusive range of values for this field
Intervals       | `*/4` or `1-5/2` | Intervals to match for this field, such as every fourth value or the range 1-5 with a step interval of 2

Example | Cron expression
--------|----------------
Build every Monday, Wednesday, and Friday at 6:00 PM | `0 18 * * Mon,Wed,Fri`, `0 18 * * 1,3,5`, or `0 18 * * 1-5/2`
Build every 6 hours | `0 0,6,12,18 * * *`, `0 */6 * * *` or `0 0-18/6 * * *`
Build every 6 hours starting at 9:00 AM | `0 9,15,21 * * *` or `0 9-21/6 * * *`

For more information on supported formats, see [Crontab Expression](https://github.com/atifaziz/NCrontab/wiki/Crontab-Expression).

### Use GitHub Copilot to create a cron expression

You can get AI assistance from GitHub Copilot to build cron expressions, or convert existing cron expressions from your local time zone to UTC.

Azure Pipelines cron schedules are defined in UTC, so schedules like **Build every Monday, Wednesday, and Friday at 6:00 PM** must be created using cron syntax, and converted from your local time zone to UTC. 

Customize the following prompts to create cron expressions, or convert cron expressions to UTC from the time zone you used to create the expressions.

In the following example, Copilot is prompted to create a UTC cron schedule to build every Monday, Wednesday, and Friday at 6:00 PM Eastern Standard Time.

```copilot-prompt
Build a UTC cron expression for Monday, Wednesday, and Friday at 6:00 PM Eastern Standard Time
```

If you already have a cron expression in your local time zone, you can ask Copilot to convert it to UTC. In this example, a cron schedule to build every Monday, Wednesday, and Friday at 6:00 PM (`0 18 * * Mon,Wed,Fri`) Eastern Standard Time is converted to UTC.

```copilot-prompt
Convert the following cron expression from Eastern Standard Time to UTC: 0 18 * * Mon,Wed,Fri
```

Converting a cron expression to UTC might require changing the days of the week in your expression. In the following example, Copilot is prompted to create a UTC cron schedule to build Monday through Friday at 12:30 AM Central European Standard Time. Central European Standard Time is ahead of UTC, so the resulting expression starts late Sunday night instead of early Monday morning, and ends on Thursday.

```copilot-prompt
Build a UTC cron expression for Monday through Friday at 12:30 AM Central European Standard Time
```

To get additional details about the cron expression generated by Copilot, you can ask Copilot to provide an explanation of the generated cron expression in your prompt.

```copilot-prompt
Build a UTC cron expression for Monday through Friday at 12:30 AM Central European Standard Time and explain the different parts of the cron expression
```

*Copilot is powered by AI, so surprises and mistakes are possible. For more information, see [Copilot general use FAQs](https://aka.ms/copilot-general-use-faqs).*

::: moniker-end

#### [Classic](#tab/classic/)

Classic schedules are defined using a graphical editor instead of cron syntax. For information on defining classic schedules, see [Examples](#examples).

* * *

## Scheduled runs view

#### [YAML](#tab/yaml/)

::: moniker range="<=azure-devops"

You can view a preview of upcoming scheduled builds by choosing **Scheduled runs** from the context menu on the [pipeline details page](../create-first-pipeline.md#view-pipeline-details) for your pipeline.

> [!IMPORTANT]
> The scheduled runs view only shows pipelines scheduled to run within seven days from the current date. If your cron schedule has an interval longer than 7 days and the next run is scheduled to start after seven days from the current date, it won't be displayed in the **Scheduled runs** view.

![Scheduled runs menu](media/triggers/scheduled-runs-menu.png)

After you create or update your scheduled triggers, you can verify them using **Scheduled runs** view.

![Scheduled runs](media/triggers/scheduled-runs.png)

This example displays the scheduled runs for the following schedule.

```yaml
schedules:
- cron: '0 0 * * *'
  displayName: Daily midnight build
  branches:
    include:
    - main
```

The **Scheduled runs** windows displays the times converted to the local time zone set on the computer used to browse to the Azure DevOps portal. This example displays a screenshot taken in the EST time zone.

> [!NOTE]
> If you update the schedule for a running pipeline, the **Scheduled runs** view isn't updated with the new schedule until the currently running pipeline completes.

::: moniker-end

#### [Classic](#tab/classic/)
::: moniker range=">= azure-devops-2020"

You can view a preview of upcoming scheduled builds by choosing **Scheduled runs** from the context menu on the [pipeline details page](../create-first-pipeline.md#view-pipeline-details) for your pipeline. 

![Scheduled runs menu](media/triggers/scheduled-runs-menu-classic.png)

After you create or update your scheduled triggers, you can verify them using this view.

![Scheduled runs](media/triggers/scheduled-runs-classic.png)

::: moniker-end

* * *

<a name="always"></a>
## Running even when there are no code changes

::: moniker range="<=azure-devops"

By default, your pipeline doesn't run as scheduled if there have been no code changes since the last successful scheduled run. For instance, consider that you've scheduled a pipeline to run every night at 9:00pm. During the weekdays, you push various changes to your code. The pipeline runs as per schedule. During the weekends, you don't make any changes to your code. If there have been no code changes since the scheduled run on Friday, then the pipeline doesn't run as scheduled during the weekend. 

::: moniker-end

#### [YAML](#tab/yaml/)

::: moniker range="<=azure-devops"

To force a pipeline to run even when there are no code changes, you can use the `always` keyword.

```yaml
schedules:
- cron: ...
  ...
  always: true
```

::: moniker-end

#### [Classic](#tab/classic/)

::: moniker range="<=azure-devops"

To configure the scheduled pipeline to build only if there has been a change since the last build, check **Only schedule builds if the source or pipeline has changed**.

![Scheduled trigger UTC + 5:30 time zone](media/triggers/scheduled-trigger-git-india.png)

::: moniker-end

* * *

<a name="limits"></a>
## Limits on the number of scheduled runs in YAML pipelines

There are certain limits on how often you can schedule a pipeline to run. These limits have been put in place to prevent misuse of Azure Pipelines resources, particularly the Microsoft-hosted agents. The limits are:
- around 1000 runs per pipeline per week
- 10 runs per pipeline per 15 minutes

::: moniker range="<=azure-devops"
## Migrating from the classic editor

The following examples show you how to migrate your schedules from the classic editor to YAML.

* [Example: Nightly build of Git repo in multiple time zones](#example-nightly-build-of-git-repo-in-multiple-time-zones)
* [Example: Nightly build with different frequencies](#example-nightly-build-with-different-frequencies)

### Example: Nightly build of Git repo in multiple time zones

In this example, the classic editor scheduled trigger has two entries, producing the following builds.

* Every Monday - Friday at 3:00 AM (UTC + 5:30 time zone), build branches that meet the `features/india/*` branch filter criteria

    ![Scheduled trigger UTC + 5:30 time zone](media/triggers/scheduled-trigger-git-india.png)

* Every Monday - Friday at 3:00 AM (UTC - 5:00 time zone), build branches that meet the `features/nc/*` branch filter criteria

    ![Scheduled trigger UTC -5:00 time zone](media/triggers/scheduled-trigger-git-nc.png)

The equivalent YAML scheduled trigger is:

```yaml
schedules:
- cron: '30 21 * * Sun-Thu'
  displayName: M-F 3:00 AM (UTC + 5:30) India daily build
  branches:
    include:
    - /features/india/*
- cron: '0 8 * * Mon-Fri'
  displayName: M-F 3:00 AM (UTC - 5) NC daily build
  branches:
    include:
    - /features/nc/*
```

In the first schedule, **M-F 3:00 AM (UTC + 5:30) India daily build**, the cron syntax (`mm HH DD MM DW`) is `30 21 * * Sun-Thu`.

* Minutes and Hours - `30 21` - This maps to `21:30 UTC` (`9:30 PM UTC`). Since the specified time zone in the classic editor is **UTC + 5:30**, we need to subtract 5 hours and 30 minutes from the desired build time of 3:00 AM to arrive at the desired UTC time to specify for the YAML trigger. [You can get AI assistance from GitHub Copilot to create your cron expression](#use-github-copilot-to-create-a-cron-expression).
* Days and Months are specified as wildcards since this schedule doesn't specify to run only on certain days of the month or on a specific month. 
* Days of the week - `Sun-Thu` - because of the timezone conversion, for our builds to run at 3:00 AM in the UTC + 5:30 India time zone, we need to specify starting them the previous day in UTC time. We could also specify the days of the week as `0-4` or `0,1,2,3,4`.

In the second schedule, **M-F 3:00 AM (UTC - 5) NC daily build**, the cron syntax is `0 8 * * Mon-Fri`.

* Minutes and Hours - `0 8` - This maps to `8:00 AM UTC`. Since the specified time zone in the classic editor is **UTC - 5:00**, we need to add 5 hours from the desired build time of 3:00 AM to arrive at the desired UTC time to specify for the YAML trigger. [You can get AI assistance from GitHub Copilot to create your cron expression](#use-github-copilot-to-create-a-cron-expression).
* Days and Months are specified as wildcards since this schedule doesn't specify to run only on certain days of the month or on a specific month. 
* Days of the week - `Mon-Fri` - Because our timezone conversions don't span multiple days of the week for our desired schedule, we don't need to do any conversion here. We could also specify the days of the week as `1-5` or `1,2,3,4,5`.

> [!IMPORTANT]
> The UTC time zones in YAML scheduled triggers don't account for daylight saving time.

> [!TIP]
> When using 3 letter days of the week and wanting a span of multiple days through Sun, Sun should be considered the first day of the week e.g. For a schedule of midnight EST, Thursday to Sunday, the cron syntax is `0 5 * * Sun,Thu-Sat`.

### Example: Nightly build with different frequencies

In this example, the classic editor scheduled trigger has two entries, producing the following builds.

* Every Monday - Friday at 3:00 AM UTC, build branches that meet the `main` and `releases/*` branch filter criteria

    ![Scheduled trigger frequency 1.](media/triggers/scheduled-trigger-git-week-day-night.png)

* Every Sunday at 3:00 AM UTC, build the `releases/lastversion` branch, even if the source or pipeline hasn't changed

    ![Scheduled trigger frequency 2.](media/triggers/scheduled-trigger-git-weekly-night.png)

The equivalent YAML scheduled trigger is:

```yaml
schedules:
- cron: '0 3 * * Mon-Fri'
  displayName: M-F 3:00 AM (UTC) daily build
  branches:
    include:
    - main
    - /releases/*
- cron: '0 3 * * Sun'
  displayName: Sunday 3:00 AM (UTC) weekly latest version build
  branches:
    include:
    - /releases/lastversion
  always: true
```

In the first schedule, **M-F 3:00 AM (UTC) daily build**, the cron syntax is `0 3 * * Mon-Fri`.

* Minutes and Hours - `0 3` - This maps to `3:00 AM UTC`. Since the specified time zone in the classic editor is **UTC**, we don't need to do any time zone conversions.
* Days and Months are specified as wildcards since this schedule doesn't specify to run only on certain days of the month or on a specific month. 
* Days of the week - `Mon-Fri` - because there's no timezone conversion, the days of the week map directly from the classic editor schedule. We could also specify the days of the week as `1,2,3,4,5`.

In the second schedule, **Sunday 3:00 AM (UTC) weekly latest version build**, the cron syntax is `0 3 * * Sun`.

* Minutes and Hours - `0 3` - This maps to `3:00 AM UTC`. Since the specified time zone in the classic editor is **UTC**, we don't need to do any time zone conversions.
* Days and Months are specified as wildcards since this schedule doesn't specify to run only on certain days of the month or on a specific month. 
* Days of the week - `Sun` - Because our timezone conversions don't span multiple days of the week for our desired schedule, we don't need to do any conversion here. We could also specify the days of the week as `0`.
* We also specify `always: true` since this build is scheduled to run whether or not the source code has been updated.

::: moniker-end

::: moniker range=">=azure-devops-2020"

## FAQ

* [I want my pipeline to run only on the schedule and not when someone pushes a change to a branch](#i-want-my-pipeline-to-run-only-on-the-schedule-and-not-when-someone-pushes-a-change-to-a-branch)
* [I defined a schedule in the YAML file. But it didn't run. What happened?](#i-defined-a-schedule-in-the-yaml-file-but-it-didnt-run-what-happened)
* [My YAML schedules were working fine. But, they stopped working now. How do I debug this?](#my-yaml-schedules-were-working-fine-but-they-stopped-working-now-how-do-i-debug-this)
* [My code hasn't changed, yet a scheduled build is triggered. Why?](#my-code-hasnt-changed-yet-a-scheduled-build-is-triggered-why)
* [I see the planned run in the Scheduled runs panel. However, it doesn't run at that time. Why?](#i-see-the-planned-run-in-the-scheduled-runs-panel-however-it-doesnt-run-at-that-time-why)
* [Schedules defined in YAML pipeline work for one branch but not the other. How do I fix this?](#schedules-defined-in-yaml-pipeline-work-for-one-branch-but-not-the-other-how-do-i-fix-this)

### I want my pipeline to run only on the schedule and not when someone pushes a change to a branch

If you want your pipeline to run only on the schedule, and not when someone pushes a change to a branch or merges a change to the main branch, you must explicitly disable the default CI and PR triggers on the pipeline.

To disable the default CI and PR triggers, add the following statements to your YAML pipeline, and [verify that you haven't overridden the YAML pipeline triggers with UI triggers](../troubleshooting/troubleshoot-triggers.md#ui-settings-override-yaml-trigger-setting).

```yaml
trigger: none
pr: none
```

For more information, see [pr definition](/azure/devops/pipelines/yaml-schema/pr) and [trigger definition](/azure/devops/pipelines/yaml-schema/trigger).

### I defined a schedule in the YAML file. But it didn't run. What happened?

* Check the next few runs that Azure Pipelines has scheduled for your pipeline. You can find these runs by selecting the **Scheduled runs** action in your pipeline. The list is filtered down to only show you the upcoming few runs over the next few days. If this doesn't meet your expectation, it's probably the case that you've mistyped your cron schedule, or you don't have the schedule defined in the correct branch. Read the topic above to understand how to configure schedules. Reevaluate your cron syntax. All the times for cron schedules are in UTC.

* Make a small trivial change to your YAML file and push that update into your repository. If there was any problem in reading the schedules from the YAML file earlier, it should be fixed now.

* If you have any schedules defined in the UI, then your YAML schedules aren't honored. Ensure that you don't have any UI schedules by navigating to the editor for your pipeline and then selecting **Triggers**.

* There's a limit on the number of runs you can schedule for a pipeline. Read more about [limits](#limits).

* If there are no changes to your code, they Azure Pipelines may not start new runs. Learn how to [override](#always) this behavior.

### My YAML schedules were working fine. But, they stopped working now. How do I debug this?

* If you didn't specify `always:true`, your pipeline won't be scheduled unless there are any updates made to your code. Check whether there have been any code changes and how you [configured the schedules](#always).

* There's a [limit](#limits) on how many times you can schedule your pipeline. Check if you've exceeded those limits.

* Check if someone enabled more schedules in the UI. Open the editor for your pipeline, and select **Triggers**. If they defined schedules in the UI, then your YAML schedules won't be honored.

* Check if your pipeline is paused or disabled. Select **Settings** for your pipeline.

* Check the next few runs that Azure Pipelines has scheduled for your pipeline. You can find these runs by selecting the **Scheduled runs** action in your pipeline. If you don't see the schedules that you expected, make a small trivial change to your YAML file, and push the update to your repository. This should resync the schedules.

* If you use GitHub for storing your code, it's possible that Azure Pipelines may have been throttled by GitHub when it tried to start a new run. Check if you can start a new run manually.

### My code hasn't changed, yet a scheduled build is triggered. Why?

* You might have enabled an option to **always** run a scheduled build even if there are no code changes. If you use a YAML file, verify the syntax for the schedule in the YAML file. If you use classic pipelines, verify if you checked this option in the scheduled triggers.

* You might have updated the build pipeline or some property of the pipeline. This will cause a new run to be scheduled even if you haven't updated your source code. Verify the **History** of changes in the pipeline using the classic editor.

* You might have updated the service connection used to connect to the repository. This will cause a new run to be scheduled even if you haven't updated your source code.

* Azure Pipelines first checks if there are any updates to your code. If Azure Pipelines is unable to reach your repository or get this information, it will create an [informational run](./information-run.md). It's a dummy build to let you know that Azure Pipelines is unable to reach your repository.

* Your pipeline may not have a completely successful build. In order to determine whether to schedule a new build or not, Azure DevOps looks up the last completely successful scheduled build. If it doesn't find one, it triggers a new scheduled build. Partially successful scheduled builds aren't considered successful, so if your pipeline only has partially successful builds, Azure DevOps will trigger scheduled builds, even if your code hasn't changed.

### I see the planned run in the Scheduled runs panel. However, it doesn't run at that time. Why?

* The **Scheduled runs** panel shows all potential schedules. However, it may not actually run unless you have made real updates to the code. To force a schedule to always run, ensure that you have set the **always** property in the YAML pipeline, or checked the option to always run in a classic pipeline.

### Schedules defined in YAML pipeline work for one branch but not the other. How do I fix this?

Schedules are defined in YAML files, and these files are associated with branches. If you want a pipeline to be scheduled for a particular branch, say `features/X`, then make sure that the YAML file **in that branch** has the cron schedule defined in it, and that it has the correct branch inclusions for the schedule. The YAML file in the `features/X` branch should have the following `schedule` in this example: 
 
```yaml
schedules: 
- cron: '0 12 * * 0'   # replace with your schedule
  branches: 
    include: 
    - features/X  
```

For more information, see [Branch considerations for scheduled triggers](#branch-considerations-for-scheduled-triggers).

::: moniker-end
