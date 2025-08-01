---
title: Settings overview for Azure DevOps
titleSuffix: Azure DevOps
description: Overview of settings available to administrators for your team, project, collection, and organization in Azure DevOps.
ms.subservice: azure-devops-settings
ms.topic: overview
ms.author: chcomley
author: chcomley
monikerRange: '<= azure-devops'
ms.date: 06/16/2025
ms.custom: sfi-image-nochange
---

# About settings for users, teams, projects, or organizations

[!INCLUDE [version-lt-eq-azure-devops](../../includes/version-lt-eq-azure-devops.md)]

::: moniker range="azure-devops"

You can configure resources for yourself, your team, project, or organization from the administrative **Settings** page. The settings available to you depend on your security group membership or administrative role.

If you're new to being a Project Administrator, see [Get started as an administrator](../../user-guide/project-admin-tutorial.md) for a comprehensive guide.

> [!NOTE]  
> You can delegate several tasks to a user with Basic or Stakeholder access by adding them to the [**Project Collection Administrators** group](../security/change-organization-collection-level-permissions.md). For more information, see [Stakeholder access quick reference](../security/stakeholder-access.md). 

::: moniker-end

::: moniker range="< azure-devops"

You configure resources either for yourself or for your team, project, or project collection from the **Settings** page. The settings you can configure depend on the security group or administrative role that you belong to.

If you're just getting started as a Project Administrator, see [Get started as an administrator](../../user-guide/project-admin-tutorial.md). 

::: moniker-end  

## User settings

Individual contributors can customize their experience in Azure DevOps by setting user preferences, enabling preview features, and managing their favorites and notifications. The following table outlines the various user settings available:

:::row:::
   :::column span="1":::
      **Area**
   :::column-end:::
   :::column span="2":::
      **Supported tasks**
   :::column-end:::
   :::column span="2":::
      **Notes**
   :::column-end:::
:::row-end:::
---
::: moniker range=">= azure-devops-2020"
:::row:::
   :::column span="1":::
      **General**
   :::column-end:::
   :::column span="2":::
      - [Set your preferences](set-your-preferences.md)
      - [Enable preview features](../../project/navigation/preview-features.md)
   :::column-end:::
   :::column span="2":::
      For an overview of default permission assignments by role, see [Default permissions and access](../security/permissions-access.md)
   :::column-end:::
:::row-end:::
---
::: moniker-end

:::row:::
   :::column span="1":::
      **Security**
   :::column-end:::
   :::column span="2":::
      - [View permissions](../security/view-permissions.md)
      - [Add an alternate account to your Visual Studio subscription](/visualstudio/subscriptions/vs-alternate-identity)
   :::column-end:::
   :::column span="2":::
      For an overview of default permission assignments by role, see [Default permissions and access](../security/permissions-access.md). 
   :::column-end:::
:::row-end:::
---
::: moniker range="azure-devops"
:::row:::
   :::column span="1":::
      **Authentication**
   :::column-end:::
   :::column span="2":::
      - [Authorize access to REST APIs with OAuth 2.0](../../integrate/get-started/authentication/oauth.md)
      - [Authenticate access with Microsoft Entra tokens](../../integrate/get-started/authentication/entra.md)
      - [Use SSH key authentication](../../repos/git/use-ssh-keys-to-authenticate.md)
      - [Authenticate access with personal access tokens](../accounts/use-personal-access-tokens-to-authenticate.md)
   :::column-end:::
   :::column span="2":::
      For an overview of supported authentication methods, see [Authentication overview](../../integrate/get-started/authentication/authentication-guidance.md).
      [!INCLUDE [use-microsoft-entra-reduce-pats](../../includes/use-microsoft-entra-reduce-pats.md)] 
   :::column-end:::
:::row-end:::
---
::: moniker-end
::: moniker range="< azure-devops"
:::row:::
   :::column span="1":::
      **Authentication**
   :::column-end:::
   :::column span="2":::
      - [Authenticate access with Microsoft Entra tokens](../../integrate/get-started/authentication/entra.md)
      - [Use SSH key authentication](../../repos/git/use-ssh-keys-to-authenticate.md)
      - [Manage OAuth app authorizations](manage-authorizations.md)
      - [Authenticate access with personal access tokens](../accounts/use-personal-access-tokens-to-authenticate.md)
   :::column-end:::
   :::column span="2":::
      For an overview of supported authentication methods, see [Authentication overview](../../repos/git/auth-overview.md). 
   :::column-end:::
:::row-end:::
---
::: moniker-end
:::row:::
   :::column span="1":::
      **Favorites**
   :::column-end:::
   :::column span="2":::
      - [Set personal or team favorites](../../project/navigation/set-favorites.md)
   :::column-end:::
   :::column span="2":::
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
      **Notifications**
   :::column-end:::
   :::column span="2":::
      - [View your subscriptions, opt-out as needed](about-settings.md)
      - [Change your preferred email address](../../organizations/notifications/change-email-address.md)
      - [Manage personal notifications](../../organizations/notifications/manage-your-personal-notifications.md)
   :::column-end:::
   :::column span="2":::
      Notifications alert you through email messages when changes occur to work items, code reviews, pull requests, source control files, builds, and more. When a project is created, many notifications are defined. If you want to opt out, you can.
   :::column-end:::
:::row-end:::
---

<a id="team"></a>

## Team administrator role and managing teams

Team administrators are responsible for configuring team resources, which primarily include Agile tools and dashboards. To configure these resources, get added as a [team administrator for the specific team](../../organizations/settings/add-team-administrator.md) or be a member of the Project Administrators or Project Collection Administrators groups.

The following table provides an overview of the Agile tools and resources that team administrators can configure. For a comprehensive guide, see [Manage teams and configure team tools](manage-teams.md).

:::row:::
   :::column span="1":::
      **Area**
   :::column-end:::
   :::column span="2":::
      **Supported tasks**
   :::column-end:::
   :::column span="2":::
      **Notes**
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
      **Team profile**
   :::column-end:::
   :::column span="2":::
      - [Add users to a project or specific team](../security/add-users-team-project.md)
      - [Add team administrators](about-settings.md)
   :::column-end:::
   :::column span="2":::
      Members of a team are included within the team group, which can be used in queries and **\@mentions** in pull requests and work item discussions.
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
     **Boards, Team configuration**
   :::column-end:::
   :::column span="2":::
      - [Backlog levels](select-backlog-navigation-levels.md?toc=/azure/devops/organizations/settings/toc.json&amp;bc=/azure/devops/organizations/settings/breadcrumb/toc.json)
      - [Show bugs on backlogs & boards](show-bugs-on-backlog.md)
      - [Configure area paths](set-area-paths.md?toc=/azure/devops/organizations/settings/toc.json&amp;bc=/azure/devops/organizations/settings/breadcrumb/toc.json)
      - [Select active iteration paths (sprints)](set-iteration-paths-sprints.md?toc=/azure/devops/organizations/settings/toc.json&amp;bc=/azure/devops/organizations/settings/breadcrumb/toc.json)
      - [Define work item templates](../../boards/backlogs/work-item-template.md?toc=/azure/devops/organizations/settings/toc.json&amp;bc=/azure/devops/organizations/settings/breadcrumb/toc.json)
   :::column-end:::
   :::column span="2":::
      For an overview of team resources, see [About teams and Agile tools](about-teams-and-settings.md). Configure boards from the board view - [Columns](../../boards/boards/add-columns.md), [Swimlanes](../../boards/boards/expedite-work.md), [Cards](../../boards/boards/customize-cards.md), [work in progress (WIP) limits](../../boards/boards/wip-limits.md). 
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
      **Dashboards**
   :::column-end:::
   :::column span="2":::
      - [Create team dashboards](../../report/dashboards/dashboards.md)
      - [Set default team dashboard permissions, manage dashboard permissions](../../report/dashboards/dashboard-permissions.md)
   :::column-end:::
   :::column span="2":::
      New dashboards added to a project are associated with a team. The default permissions allow team members to create and edit dashboards for their team.
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
      **Notifications**
   :::column-end:::
   :::column span="2":::
      - [Manage team notifications](../../organizations/notifications/manage-team-group-global-organization-notifications.md)
   :::column-end:::
   :::column span="2":::
      Many team notifications are automatically defined when a team is added. For more information about how notifications are managed, see [About notifications](../../organizations/notifications/about-notifications.md).
   :::column-end:::
:::row-end:::
---

<a id="project"></a>

## Project Administrator role and managing projects

Members of the [**Project Administrators** group](../security/change-project-level-permissions.md) configure resources for a project and manage permissions at the project-level. Members of the [**Project Collection Administrators** group](../security/change-organization-collection-level-permissions.md) can configure team settings as well.

See also [Get started as an administrator](../../user-guide/project-admin-tutorial.md).

::: moniker range="azure-devops"
**Project settings**  
From the administrative **Project settings** page, you can configure settings available from the tabs shown in the following image. 
> [!div class="mx-imgBorder"]  
> ![Screenshot of Project settings, new navigation.](media/about/project-settings-new-nav.png) 
::: moniker-end

::: moniker range="azure-devops-2022"
**Project-level settings**  
From the administrative **Project settings** page, you can configure settings available from the tabs shown in the following image.

![Screenshot of Project settings page, Azure DevOps Server 2022.](media/about/project-settings-server-2022.png)  
::: moniker-end

::: moniker range="<azure-devops-2022"
**Project-level settings**  
From the administrative **Project settings** page, you can configure settings available from the tabs shown in the following image.

![Screenshot of Project settings page, Azure DevOps Server versions.](media/about/project-settings-server-2020.png)  
::: moniker-end

:::row:::
   :::column span="1":::
     **Area**
   :::column-end:::
   :::column span="2":::
      **Supported tasks**
   :::column-end:::
   :::column span="2":::
      **Notes**
   :::column-end:::
:::row-end:::
---
::: moniker range="azure-devops"
:::row:::
   :::column span="1":::
      **General**
   :::column-end:::
   :::column span="2":::
      - Set project description
      - [Change the project visibility, public or private](../projects/make-project-public.md)
   :::column-end:::
   :::column span="2":::
      Update the project description or change its visibility.
   :::column-end:::
:::row-end:::
---
::: moniker-end
::: moniker range="< azure-devops"
:::row:::
   :::column span="1":::
      **General**
   :::column-end:::
   :::column span="2":::
      - Set project description
   :::column-end:::
   :::column span="2":::
      Update the project description or change its visibility.
   :::column-end:::
:::row-end:::
---
::: moniker-end
::: moniker range="<=azure-devops"
:::row:::
   :::column span="1":::
      **Services**
   :::column-end:::
   :::column span="2":::
      - [Turn a service on or off](set-services.md)
   :::column-end:::
   :::column span="2":::
      Services that aren't used by project members can be disabled so that they don't appear in the web portal. Turning off a service removes the service from the user interface for all project users. However, data defined for the service is preserved and available if you later decide to turn on the service.
   :::column-end:::
:::row-end:::
---
::: moniker-end
:::row:::
   :::column span="1":::
      **Teams**
   :::column-end:::
   :::column span="2":::
      - [Add another team and team members](add-teams.md)
      - [Add a team administrator](add-team-administrator.md)
   :::column-end:::
   :::column span="2":::
            When you create a project, Azure DevOps automatically creates a default team. You can add more teams to give specific groups of users their own set of Agile tools, which they can fully configure and manage. Each team gets access to its own product backlog, portfolio backlogs, sprint backlogs, dashboards, team-scoped widgets, and more. For a complete overview of all tools available to teams, see [About teams and Agile tools](about-teams-and-settings.md).
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
      **Security**
   :::column-end:::
   :::column span="2":::
      - [Add user to a project](../security/add-users-team-project.md)
      - [Add a team administrator](add-team-administrator.md)
      - [Request an increase in permission levels](../security/request-changes-permissions.md)
      - [Look up a project administrator](../security/look-up-project-administrators.md)
      - [Change project-level permissions](../security/change-project-level-permissions.md)
      - [Set object-level permissions](../security/set-object-level-permissions.md)
      - [Grant or restrict permissions to select tasks](../security/restrict-access.md)
      - [Set dashboard permissions](../security/../../report/dashboards/dashboard-permissions.md)
      - [Set Wiki permissions](../../project/wiki/manage-readme-wiki-permissions.md)
      - [Set feedback permissions](/previous-versions/azure/devops/project/feedback/give-permissions-feedback)
      - [Set build and release permissions](../../pipelines/policies/permissions.md#pipeline-permissions)
   :::column-end:::
   :::column span="2":::
      Project Administrators can add users to a project or a team. Adding a user to a team also adds them to the project. Users added at the project level can view and contribute only to that specific project.
      For an overview of security concepts, see [Get started with permissions, access, and security groups](../security/about-permissions.md) and [About access levels](../security/access-levels.md). For a list of project-level permissions, see [Permissions and groups reference, Project-level permissions](../security/permissions.md#project-level-permissions).
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
      **Notifications**
   :::column-end:::
   :::column span="2":::
      - [Manage project-level notifications](../../organizations/notifications/manage-team-group-global-organization-notifications.md)
   :::column-end:::
   :::column span="2":::
      Many project-level notifications are set up automatically when you create a project. You manage project-level notifications in the same way as [team-level notifications](../../organizations/notifications/manage-team-group-global-organization-notifications.md).
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
      **Service hooks**
   :::column-end:::
   :::column span="2":::
      - [Configure service hooks](../../service-hooks/overview.md)
   :::column-end:::
   :::column span="2":::
      With service hooks, you can automate a task on other services, such as [Trello, Datadog, and more](../../service-hooks/overview.md). You can use service hooks in custom apps and services to drive activities as events happen.
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
      **Dashboards**
   :::column-end:::
   :::column span="2":::
      - [Set default dashboard permissions](../../report/dashboards/dashboard-permissions.md)
   :::column-end:::
   :::column span="2":::
      New dashboards added to a project automatically inherit the default dashboard permissions. By default, team members have permission to create and edit dashboards for their team.
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
      **Boards, Project configuration**
   :::column-end:::
   :::column span="2":::
      - [Define area paths](set-area-paths.md)
      - [Define iteration paths or sprints](set-iteration-paths-sprints.md)
   :::column-end:::
   :::column span="2":::
      Area and iteration paths set at the project level are then used to set team defaults. To configure more product backlogs, boards, and dashboards, you first [add a team](add-teams.md).
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
      **Build and release (Agent Pools, Release)**
   :::column-end:::
   :::column span="2":::
      - [Manage Agent queues and agent pools](../../pipelines/agents/pools-queues.md)
      - [Manage service connections](../../pipelines/library/service-endpoints.md)
      - [Manage deployment pools and groups](../../pipelines/release/deployment-groups/index.md)
      - [Set retention policies](../../pipelines/policies/retention.md)
   :::column-end:::
   :::column span="2":::
      Area and iteration paths defined at the project level serve as defaults for teams. To configure more product backlogs, boards, or dashboards for specific groups, first [add a team](add-teams.md).
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
      **Repos, Code version control**
   :::column-end:::
   :::column span="2":::
      - [Create Git repositories](../../repos/git/creatingrepo.md)
      - [Set Git repository permissions](../../repos/git/set-git-repository-permissions.md)
      - [Set TFVC repository permissions](../../repos/tfvc/set-tfvc-repository-permissions.md)
      - [Manage branch policies](../../repos/git/branch-policies.md)
      - [Add Team Foundation Version Control (TFVC) Check-In Policies](../../repos/tfvc/add-check-policies.md)
   :::column-end:::
   :::column span="2":::
      You can manage code using [Git repositories](../../repos/git/index.yml) or one [TFVC repository.](../../repos/tfvc/index.yml).
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
      **Test**
   :::column-end:::
   :::column span="2":::
      - [Set test retention policies](../../test/how-long-to-keep-test-results.md)
      - [Manage test-related permissions at project level](../security/change-project-level-permissions.md)
      - [Set area path-level test permissions](../security/set-permissions-access-work-tracking.md#set-permissions-area-path)
   :::column-end:::
   :::column span="2":::
      Manual testing relies on work item types to create and manage test plans, test suites, test cases, shared steps, and shared parameters. You can customize the test plans, test suites, and test cases using an inherited process. For more information, see [Customize a process](work/customize-process.md).
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
      **Wiki**
   :::column-end:::
   :::column span="2":::
      - [Create a wiki for your project](../../project/wiki/wiki-create-repo.md)
      - [Publish a Git repository to a wiki](../../project/wiki/publish-repo-to-wiki.md)
      - [Manage README and Wiki permissions](../../project/wiki/manage-readme-wiki-permissions.md)
   :::column-end:::
   :::column span="2":::
      To share information with your team, you can use Markdown format within a project Wiki, within your project README file, or other repository README file. For more information, see [About READMes and Wikis](../../project/wiki/about-readme-wiki.md).
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
      **Extensions**
   :::column-end:::
   :::column span="2":::
      - [Request a Marketplace extension](../../marketplace/request-extensions.md)
   :::column-end:::
   :::column span="2":::
      Individual contributors and project administrators can request the installation of a Marketplace extension. However, only members of the Project Collection Administrators group can approve and install these extensions.
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
      **Team configuration**
   :::column-end:::
   :::column span="2":::
      - [Manage and configure team tools](manage-teams.md)
      - [Manage notifications](../../organizations/notifications/manage-team-group-global-organization-notifications.md)
   :::column-end:::
   :::column span="2":::
      For more information, see [About teams and Agile tools](about-teams-and-settings.md).
   :::column-end:::
:::row-end:::
---
::: moniker range="azure-devops"
:::row:::
   :::column span="1":::
      **GitHub connections**
   :::column-end:::
   :::column span="2":::
      - [Connect Azure Boards to GitHub](../../boards/github/connect-to-github.md)
      - [Install and configure Azure Boards app for GitHub](../../boards/github/install-github-app.md)
      - [Link GitHub commits, pull requests, and issues to work items](../../boards/github/link-to-from-github.md)
   :::column-end:::
   :::column span="2":::
      By connecting your Azure Boards project to GitHub.com repositories, you enable linking between GitHub commits, pull requests, and Azure Boards work items. This integration allows you to use GitHub for source code development while using Azure Boards to plan and track your work.
   :::column-end:::
:::row-end:::
---
::: moniker-end
:::row:::
   :::column span="1":::
      **Service connections**
   :::column-end:::
   :::column span="2":::
      - [Manage service connections in Azure Pipelines](../../pipelines/policies/permissions.md#set-service-connection-project-permissions)
   :::column-end:::
   :::column span="2":::
      For more information, see a [list of common service connection types](../../pipelines/library/service-endpoints.md#common-service-connection-types).
   :::column-end:::
:::row-end:::
---

<a id="admin"></a>

## Project Collection Administrator (PCA) role and managing collections of projects 

Members of the [**Project Collection Administrators** group](../security/change-organization-collection-level-permissions.md) manage resources and settings for all projects within an organization or collection. They have full permissions to add and manage projects, configure resources, and set permissions at the collection, project, team, or object level.

::: moniker range="azure-devops"
  
**Organization settings**  
From the administrative **Organization settings** page, you can configure settings available from the tabs shown in the following image and table. 

> [!NOTE]  
> If the **Limit user visibility and collaboration to specific projects** preview feature is enabled for the organization, users added to the **Project-Scoped Users** group can't access **Organization Settings** other than the **Overview** and **Projects** pages. For more information including important security-related call-outs, see [Manage your organization, Limit  user visibility for projects and more](../../user-guide/manage-organization-collection.md#project-scoped-user-group). 

> [!div class="mx-imgBorder"]  
> ![Screenshot of Organization settings options, cloud.](media/about/organization-settings-options-cloud.png) 

::: moniker-end

::: moniker range="azure-devops-2022"
**Collection-level settings**  
From the administrative page for a collection, you can configure the settings shown in the following image. 

:::image type="content" source="media/about/collection-settings-2022.png" alt-text="Screenshot of Collection settings options, Azure DevOps Server 2022.":::

::: moniker-end

::: moniker range="<azure-devops-2022"
**Collection-level settings**  

From the administrative page for a collection, you can configure the settings shown in the following image. 

![Screenshot of Collection settings options, Azure DevOps Server 2019-2020 versions.](media/about/collection-settings-options-server-versions.png) 

::: moniker-end

::: moniker range="azure-devops"

For an overview of managing your organization, see [About organization management](../accounts/organization-management.md).

::: moniker-end

::: moniker range="< azure-devops" 
For an overview of managing collections, see [Configure and manage Azure DevOps Server resources](/azure/devops/server/admin/admin-quick-ref).
::: moniker-end 

:::row:::
   :::column span="1":::
      **Area**
   :::column-end:::
   :::column span="2":::
      **Supported tasks**
   :::column-end:::
   :::column span="2":::
      **Notes**
   :::column-end:::
:::row-end:::
---
::: moniker range=">= azure-devops-2020"
:::row:::
   :::column span="1":::
      **Preview features**
   :::column-end:::
   :::column span="2":::
      - [Manage and enable preview features](../../project/navigation/preview-features.md)
   :::column-end:::
   :::column span="2":::
      Organization administrators can enable or disable organization-level or collection-level features that are in preview.
   :::column-end:::
:::row-end:::
---
::: moniker-end
::: moniker range="azure-devops"
:::row:::
   :::column span="1":::
      **Overview**
   :::column-end:::
   :::column span="2":::
      - Add and manage organization information: [change organization owner](../accounts/change-organization-ownership.md), [Rename](../accounts/rename-organization.md), [Delete](../accounts/delete-your-organization.md)- [Recover](../accounts/recover-your-organization.md), [Find or change your organization location](../accounts/change-organization-location.md)
      - [Set up billing](../billing/set-up-billing-for-your-organization-vs.md#set-up-billing)
   :::column-end:::
   :::column span="2":::
      From the **Overview** page, you can manage the time zone, owner, region, and other settings that apply to all projects.
   :::column-end:::
:::row-end:::
---
::: moniker-end
:::row:::
   :::column span="1":::
      **Projects**
   :::column-end:::
   :::column span="2":::
      - Add and manage projects: [Create](../projects/create-project.md), [Rename](../projects/rename-project.md), [Delete](../projects/delete-project.md)
      - [Add users to projects](../security/add-users-team-project.md)
      - [Save project data](../projects/save-project-data.md)
   :::column-end:::
   :::column span="2":::
      A project provides the fundamental resource for storing your code, managing your CI/CD operations, and planning and tracking work for your project. In general, minimize the number of projects you create, to keep things simple. For more information, see [About projects and scaling your organization](../projects/about-projects.md).
   :::column-end:::
:::row-end:::
---
::: moniker range="azure-devops"
:::row:::
   :::column span="1":::
      **Users**
   :::column-end:::
   :::column span="2":::
      - [Add and manage users](../accounts/add-organization-users.md)
      - [Add external users](../accounts/add-external-user.md)
      - [Remove users](../accounts/delete-organization-users.md)
   :::column-end:::
   :::column span="2":::
      For large organizations with a sizable number of users, we recommend that you [manage user access through Microsoft Entra ID](../accounts/access-with-azure-ad.md). For a few users, you can manage user access by adding their Microsoft Service Account (MSA) email. From the account-level Users page, you can also [export the set of users and their access levels](../security/export-users-audit-log.md).
   :::column-end:::
:::row-end:::
---
::: moniker-end
::: moniker range="azure-devops"
:::row:::
   :::column span="1":::
      **Billing**
   :::column-end:::
   :::column span="2":::
      - [Set up billing](../billing/set-up-billing-for-your-organization-vs.md#set-up-billing)
      - [Try Azure Test Plans for free](../billing/try-additional-features-vs.md)
      - [Pay for users (Basic)](../billing/buy-basic-access-add-users.md)
      - [Buy parallel jobs](../../pipelines/licensing/concurrent-jobs.md#how-much-do-parallel-jobs-cost)
      - [Add a user to make purchases](../billing/set-up-billing-for-your-organization-vs.md#give-a-user-access-to-manage-billing)
   :::column-end:::
   :::column span="2":::
      All billing gets managed through Azure. For more information, see [Billing overview](../billing/overview.md).
   :::column-end:::
:::row-end:::
---
::: moniker-end
::: moniker range="azure-devops"
:::row:::
   :::column span="1":::
      **Auditing**
   :::column-end:::
   :::column span="2":::
      - [Access, export, and filter audit logs](../audit/azure-devops-auditing.md)
      - [Create audit streaming](../audit/auditing-streaming.md)
   :::column-end:::
   :::column span="2":::
      The auditing page provides a simple view into the audit events recorded for your organization. For more information, see [Review audit log](../audit/azure-devops-auditing.md#review-audit-log), [Export audit events](../audit/azure-devops-auditing.md#export-audit-events), or learn more about Audit [events](../audit/auditing-events.md).
   :::column-end:::
:::row-end:::
---
::: moniker-end
:::row:::
   :::column span="1":::
      **Global notifications**
   :::column-end:::
   :::column span="2":::
      - [Manage collection-level notifications](../../organizations/notifications/manage-team-group-global-organization-notifications.md)
   :::column-end:::
   :::column span="2":::
      Many notifications are automatically defined when an organization is added. Notifications at the organization-level are managed in much the same way as they are at the [team level](../../organizations/notifications/manage-team-group-global-organization-notifications.md).
   :::column-end:::
:::row-end:::
---
::: moniker range="azure-devops"
:::row:::
   :::column span="1":::
      **Usage**
   :::column-end:::
   :::column span="2":::
      - [Monitor usage](../../integrate/concepts/rate-limits.md)
   :::column-end:::
   :::column span="2":::
      Certain rate limits are in place to ensure performance across the cloud service platform.
   :::column-end:::
:::row-end:::
---
::: moniker-end
:::row:::
   :::column span="1":::
      **Extensions**
   :::column-end:::
   :::column span="2":::
      - [Install and manage Marketplace extensions](../../marketplace/install-extension.md)
      - [Approve extensions](../../marketplace/request-extensions.md)
      - [Grant permissions to manage extensions](../../marketplace/grant-permissions.md)
      - [Uninstall or disable extensions](../../marketplace/install-extension.md#uninstall-an-extension)
   :::column-end:::
   :::column span="2":::
      An extension is an installable unit that contributes new capabilities to your projects. You can find extensions from within the [Visual Studio Marketplace](https://marketplace.visualstudio.com/azuredevops) in the Azure DevOps tab to support planning and tracking of work items, sprints, scrums, and so on; build and release flows; code testing and tracking; and collaboration among team members.
   :::column-end:::
:::row-end:::
---
::: moniker range="azure-devops"
:::row:::
   :::column span="1":::
      **Security: Policies**
   :::column-end:::
   :::column span="2":::
      - [Manage application access policies](../accounts/change-application-access-policies.md)
      - [Add external users](../accounts/add-external-user.md)   
      - [Disable Request Access policy](../accounts/disable-request-access-policy.md)
      - [Restrict users from creating new organizations with Microsoft Entra policy](../accounts/azure-ad-tenant-policy-restrict-org-creation.md)
      - [Restrict Team and Project Administrators from inviting new users](../security/restrict-invitations.md)
      - [Enable Conditional Access or Multi-Factor Authentication](/azure/active-directory/authentication/tutorial-enable-azure-mfa)
   :::column-end:::
   :::column span="2":::
      Set policies to allow or disallow access by other applications or services to the organization.
   :::column-end:::
:::row-end:::
---
::: moniker-end
::: moniker range="azure-devops"
:::row:::
   :::column span="1":::
      **Security: Permissions**
   :::column-end:::
   :::column span="2":::
      - [Look up the organization owner](../security/look-up-organization-owner.md)
      - [Look up a project collection administrator ](../security/look-up-project-collection-administrators.md)
      - [Add administrators, set organization-level permissions](../security/change-organization-collection-level-permissions.md)
      - [Add Microsoft Entra groups](../accounts/manage-azure-active-directory-groups.md)
      - [Connect to Microsoft Entra ID](../accounts/connect-organization-to-azure-ad.md)
      - [Set permissions to manage extensions](../../marketplace/grant-permissions.md)
      - [Manage conditional access](../accounts/change-application-access-policies.md)
   :::column-end:::
   :::column span="2":::
      For an overview of security concepts, see [Get started with permissions, access, and security groups](../security/about-permissions.md) and [About access levels](../security/access-levels.md). For a list of collection-level permissions, see [Permissions and groups reference, Collection-level permissions](../security/permissions.md#organization-level-permissions).
   :::column-end:::
:::row-end:::
---
::: moniker-end
::: moniker range="< azure-devops"
:::row:::
   :::column span="1":::
      **Security**
   :::column-end:::
   :::column span="2":::
      - [Look up the organization owner](../security/look-up-organization-owner.md)
      - [Look up a project collection administrator ](../security/look-up-project-collection-administrators.md)
      - [Add administrators, set organization-level permissions](../security/change-organization-collection-level-permissions.md)
      - [Manage access to specific features](../security/restrict-access.md) 
   :::column-end:::
   :::column span="2":::
      For an overview of security concepts, see [Get started with permissions, access, and security groups](../security/about-permissions.md) and [About access levels](../security/access-levels.md). For a list of collection-level permissions, see [Permissions and groups reference, Collection-level permissions](../security/permissions.md#organization-level-permissions).
   :::column-end:::
:::row-end:::
---
::: moniker-end
::: moniker range="<=azure-devops"
:::row:::
   :::column span="1":::
      **Boards: Process**
   :::column-end:::
   :::column span="2":::
      - [Customize a project](work/customize-process.md)
      - [Add and manage processes](work/manage-process.md)
   :::column-end:::
   :::column span="2":::
      Process customization applies to Azure Boards only. You can customize the Agile tools and work tracking artifacts. Create and customize an inherited process, and then update the project to use that process. For more information, see [About process customization and inherited processes](work/inheritance-process-model.md).
   :::column-end:::
:::row-end:::
---
::: moniker-end
:::row:::
   :::column span="1":::
      **Pipelines**<br/>**Build and release**
   :::column-end:::
   :::column span="2":::
      - [Set retention policies](../../pipelines/policies/retention.md)
      - [Set resource limits for pipelines](../../pipelines/licensing/concurrent-jobs.md)
      - [Add and manage agent pools](../../pipelines/agents/pools-queues.md)
      - [Add and manage deployment pools](../../pipelines/release/deployment-groups/index.md)
   :::column-end:::
   :::column span="2":::
     You manage resources that support CI/CD operations for all projects through the **Agent pools**, **Deployment pools**, and **Retention and limits** pages.
   :::column-end:::
:::row-end:::
---
::: moniker range="azure-devops"
:::row:::
   :::column span="1":::
      **Artifact storage**
   :::column-end:::
   :::column span="2":::
      - [Delete and recover packages in Azure Artifacts](../../artifacts/how-to/delete-and-recover-packages.md)
      - [Artifacts storage consumption](../../artifacts/artifact-storage.md)
   :::column-end:::
   :::column span="2":::
     Each organization gets Azure Artifacts for free, up until 2 GB of storage is reached. For more information, see [Start using Azure Artifacts](../../artifacts/start-using-azure-artifacts.md#increase-artifacts-storage-limit).
   :::column-end:::
:::row-end:::
---
::: moniker-end

::: moniker range="< azure-devops"

<a id="admin"></a>

## Server Administrator role 

Members of the [Team Foundation Server Administrators group](/azure/devops/server/admin/add-administrator) configure resources for all project collections. They also can do all tasks to administer projects, collections, and server instances.     

Server Administrators set access levels for a user or security group via the web portal. See [Change access levels](../security/change-access-levels.md). 

For more information, see [Team Foundation Server Administration Documentation](/azure/devops/server/server).

::: moniker-end

## Related content

- [Add or update information banners](manage-banners.md)
- [Review resources granted to project members](../projects/resources-granted-to-project-members.md)
- [Configure permissions and groups](../security/permissions.md)
- [Manage your project](../../user-guide/project-admin-tutorial.md)
- [Manage your organization or project collection](../../user-guide/manage-organization-collection.md)
- [Monitor and manage rate limits](../../integrate/concepts/rate-limits.md)
