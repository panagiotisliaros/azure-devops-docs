---
title: Add artifact or team
titleSuffix: Azure DevOps
description: How to add a new artifact, view, or team within the web portal in Azure DevOps
ms.custom: navigation
ms.subservice: azure-devops-projects 
ms.author: chcomley
author: chcomley
ms.topic: how-to
monikerRange: '<= azure-devops'
ms.date: 04/04/2022
---

# Add an artifact or team artifacts

[!INCLUDE [version-lt-eq-azure-devops](../../includes/version-lt-eq-azure-devops.md)] 

Select the service of interest to get started adding new artifacts or objects. For example, to add work items, choose **Boards** or **Work**. Some artifacts&mdash;such as a product backlog, board, portfolio backlogs&mdash;are added when you add a team.  

Prior to adding an artifact, make sure that you've [selected the project and repository](go-to-project-repo.md) that you want to work in.  

## Prerequisites

[!INCLUDE [prerequisites](../../boards/includes/prerequisites.md)]

There might be other prerequisites for managing specific items. For more information, see [Security groups, service accounts, and permissions reference](../../organizations/security/permissions.md).

## Add work items, queries, or other work tracking artifacts 

You can quickly add a query or work item when working from a **Boards** or **Work** page. 

Choose a **Boards** page&mdash;such as **Work Items**, **Boards**, or **Backlogs**. Then choose the :::image type="icon" source="../../media/icons/blue-add.png" border="false"::: plus icon and select from the menu of options. 

> [!div class="mx-imgBorder"]
> ![Work, add artifact](media/add-artifact/add-work-item-query-vert.png)

To add other work tracking artifacts, see one of the following articles: 

- To add a board, backlog, or sprint backlog, first [add a team](../../organizations/settings/add-teams.md) which will be associated with those artifacts 
- [Add a delivery plan](../../boards/plans/review-team-plans.md)
- [Add a managed work item query](../../boards/queries/using-queries.md) 
- [Add work items](../../boards/work-items/view-add-work-items.md).

## Add a pull request or Git repository 

You can quickly add a pull request, Git repository, or work item using the **Add** menu when working from **Code**. 

Expand the **Repos** service and choose **Files**, **Commits**, or **Pull Requests** (Git repos) or **Files**, **Changesets**, or **Shelvesets** (TFVC). Then, choose the :::image type="icon" source="../../media/icons/blue-add.png" border="false"::: plus icon and select from the menu of options. 

> [!div class="mx-imgBorder"]
> ![Add artifact](media/add-artifact/add-repo-vert.png)

For details on adding a Git repository, see [Git repository](../../repos/git/creatingrepo.md). 

Note that you can only add one TFVC repository per project, but an unlimited number of Git repositories. To learn more about Git artifacts, see one of the following articles:

- [Git repository](../../repos/git/creatingrepo.md)
- [Git branch](../../repos/git/create-branch.md)
- [Git pull request](../../repos/git/pull-requests.md) 
- [Add work items](../../boards/work-items/view-add-work-items.md)

## Add build and release pipelines 

Expand  **Pipelines** and choose **Builds** or **Releases**. Then choose the :::image type="icon" source="../../media/icons/blue-add.png" border="false"::: plus icon and select from the menu of options. 

> [!div class="mx-imgBorder"]
> ![Add build and release pipelines.](media/add-artifact/add-pipeline-vert.png)

For more information about adding other pipeline related artifacts, see the following articles: 
- [Deployment groups](../../pipelines/release/deployment-groups/index.md)  
- [Task groups](../../pipelines/library/task-groups.md)  
- [Variable groups](../../pipelines/library/variable-groups.md)  
- [Secure files](../../pipelines/library/secure-files.md)  

## Add a team 

Agile tools and dashboards are typically associated with teams. You add teams to a project. To learn more about teams, see [About teams and Agile tools](../../organizations/settings/about-teams-and-settings.md). To add a team, see [Add a team and team members](../../organizations/settings/add-teams.md). 

<a id="view-teams"></a>

## View teams already defined 

To view the set of defined teams, open **Project settings**, and choose **Overview**.  

> [!div class="mx-imgBorder"]  
> ![Web portal, Project Settings, Teams](media/add-artifact/view-teams-vert-brn.png)

## Add a dashboard 

::: moniker range=">= azure-devops-2020"
Dashboards are associated with a team or a project. Each team can create and configure a number of dashboards. And, any team member can create one or more project dashboards. To learn how, see [Add a dashboard](../../report/dashboards/dashboards.md).
::: moniker-end

## Add a wiki 

If you don't have a wiki yet, you can add one. Once added, you can add and update pages to that wiki. 

- [Create a wiki](../wiki/wiki-create-repo.md)
- [Add and edit wiki pages](../wiki/add-edit-wiki.md)
- [Publish a Git repository to a wiki](../wiki/publish-repo-to-wiki.md)

## Related content

- [Azure Artifacts](../../artifacts/index.yml)  
- [Exploratory & Manual Testing](../../test/index.yml)
