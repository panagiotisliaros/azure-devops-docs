---
title: Permissions, licensing, and access for manual testing
description: Default permissions and access levels in Azure DevOps for manual and exploratory testing and problems.
ms.assetid: 91146CFD-A4CE-4CC5-973D-1633419CAFDE
ms.service: azure-devops-test-plans
ms.custom: UpdateFrequency3
ms.topic: reference
ms.author: jeom
author: rohit-batra
monikerRange: '<= azure-devops'
ms.date: 09/15/2021
ms.update-cycle: 1095-days
---

# Manual test access and permissions 

[!INCLUDE [version-lt-eq-azure-devops](../includes/version-lt-eq-azure-devops.md)]

Access levels and permissions control access to Azure Test Plans features. 

## Prerequisites

| Category | Requirement |
|--------------|-------------|
| **Project access** | [Project member](../organizations/security/add-users-team-project.md). |
| **Access levels** |- To access the Test Plans web portal: At least **Basic** access.<br>- To define and manage test plans, test suites, and test cases: **Basic + Test Plans** access.|

> [!NOTE]  
> Users granted **Stakeholder** access have no access to features or functions supported through the Test Plans or Test web portal. However, they can provide feedback through the **Test & Feedback** extension. For more information, see [Stakeholder access quick reference](../organizations/security/stakeholder-access.md).

## Access and licensing 

To exercise the full range of test-related features, have [Basic + Test Plans](../organizations/billing/buy-access-tfs-test-hub.md) access level or have one of the following subscriptions:
	- [Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/enterprise/)
	- [Visual Studio Test Professional](https://visualstudio.microsoft.com/vs/test-professional/)
	- [MSDN Platform](https://visualstudio.microsoft.com/msdn-platforms/)

Users who have one of the above subscriptions can exercise all Test Plans features for no extra charge. For more information, see [Compare Visual Studio subscriptions](https://www.visualstudio.com/vs/pricing).
 
Nonsubscribers must purchase **Basic + Test Plans** to use Test Plans, which can be for any specified number of users.

> [!IMPORTANT]  
> Manual testers can execute tests with **Basic** access. Licenses for this extension also give users rights to use [Microsoft Test Manager](/previous-versions/azure/devops/test/mtm/guidance-mtm-usage) (a deprecated on-premises client).

The following table summarizes the license requirements required to exercise select tasks. 

| Task  | Access level|
| --- | --- |
| Provide feedback | Stakeholder | 
| Execute tests, Mark test outcomes | Basic |
| Chart tasks, View reports | Basic |
| Create and manage test plans and test suites | Basic + Test Plans  |
| Author test cases using a grid-like view and edit in the Test Runner | Basic + Test Plans  |
| Assign test cases to suites, move test cases, and order test cases | Basic + Test Plans  |
| Prepare for execution such as assigning configurations or testers | Basic + Test Plans  | 
| Prepare User Acceptance Testing | Basic + Test Plans  |

<a id="access-by-user-role"></a>

## Permissions

In addition to having the necessary access level, you also need the necessary permissions to exercise select tasks. Because manual testing is managed through [test-specific work item types](test-objects-overview.md), they're subject to some of the same permissions that manage work items.  

The following table provides the default permissions assigned to the built-in security groups: **Readers**, **Contributors**, and **Project Administrators**. Permissions are assigned for Area Paths and at the project-level. To learn how, see [Set permissions and access for testing](../organizations/security/set-permissions-access-test.md). 


[!INCLUDE [test](../organizations/security/includes/test.md)] 

For a simplified view of all default permissions assigned to built-in groups, see [Default permissions and access](../organizations/security/permissions-access.md).  
 
## Related content

- [Test objects and terms](test-objects-overview.md)  
- [Set permissions and access for manual testing](../organizations/security/set-permissions-access-test.md)  
- [Default permissions and access](../organizations/security/permissions-access.md)  
- [Security groups, service accounts, and permissions in Azure DevOps](../organizations/security/permissions.md)
