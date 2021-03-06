---
title: 工作流托管选项
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f022a5162ab8624d0c696efde6416484e77e874
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2018
---
# <a name="workflow-hosting-options"></a>工作流托管选项
大多数 Windows Workflow Foundation (WF) 示例使用控制台应用程序中承载的工作流，但这并非现实世界工作流的一个现实的方案。 实际业务应用程序中的工作流将会承载在恒定进程中 — 或是由开发人员编写的 Windows 服务，或是诸如 [!INCLUDE[iisver](../../../includes/iisver-md.md)] 或 AppFabric 之类的服务器应用程序。 这些方法之间的区别如下。  
  
## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>用配有 Windows AppFabric 的 IIS 承载工作流  
 用配有 AppFabric 的 IIS 是承载工作流的首选方法。 用 AppFabric 来承载工作流的应用程序是 Windows Activation Service，它解除了仅通过 IIS 对 HTTP 的依赖。  
  
## <a name="hosting-workflows-in-iis-alone"></a>仅用 IIS 来承载工作流  
 不建议仅用 [!INCLUDE[iisver](../../../includes/iisver-md.md)]，因为 AppFabric 有管理和监视工具，便于对运行中的应用程序进行维护。 仅当有支持迁移到 AppFabric 的基础结构时，才应将工作流单独承载在 [!INCLUDE[iisver](../../../includes/iisver-md.md)] 中。  
  
> [!WARNING]
>  由于各种原因，[!INCLUDE[iisver](../../../includes/iisver-md.md)] 定期对应用程序池进行回收。 当应用程序池被回收时，IIS 即停止接受发给旧应用程序池的消息，并实例化一个新的应用程序池以接受新请求。 如果工作流在发出响应后继续运行，则 [!INCLUDE[iisver](../../../includes/iisver-md.md)] 不会知道正在运行的任务，可能会将宿主应用程序池回收掉。 如果发生这种情况，将中止工作流，并跟踪服务将记录[1004-WorkflowInstanceAborted](../../../docs/framework/windows-workflow-foundation/1004-workflowinstanceaborted.md)使用空的原因字段的消息。  
>   
>  如果使用了持久化机制，则主机必须显式地从上一个持久化点重启被中止的实例。  
>   
>  如果使用了 AppFabric，则工作流管理服务最终将从上次成功持久化的点恢复工作流（如果使用了持久化机制）。 如果未使用持久化机制，则该工作流执行非“请求/响应”模式的操作，当工作流中止时，数据也将丢失。  
  
## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>在自定义 Windows 服务中承载工作流  
 若要创建自定义工作流服务来承载工作流，要求开发人员复制 AppFabric 自带的许多功能，但允许通过自定义功能实现更大的灵活性。 仅当 AppFabric 经证不合适时，才应考虑这一选项。
