---
title: WF 中的控制流活动
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 91fb4e18d753709ab973730300ffef5a952c56d6
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="control-flow-activities-in-wf"></a>WF 中的控制流活动
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]提供用于控制工作流中执行流的多个活动。 某些这些活动 (如`Switch`和`If`) 实现与编程环境，如 Visual C# 中，同时其他类似的流控制结构 (如`Pick`) 建立新编程结构的模型。  
  
 请注意，当诸如 `Parallel` 和 `ParallelForEach` 活动之类的活动计划同时执行多个子活动时，一个工作流只能使用单个线程。 这些活动的每个子活动都按顺序执行，并在前面的活动完成或变为空闲之前，不会执行后续活动。 因此，这些活动对于某些应用程序来说最有用，这些应用程序中的多个可能阻止执行的活动必须采用交错的方式执行。 如果这些活动中没有任何子活动变为空闲，则 `Parallel` 活动执行方式就像 `Sequence` 活动一样，并且 `ParallelForEach` 活动执行方式就像 `ForEach` 活动一样。 然而，如果使用异步活动（例如从 <xref:System.Activities.AsyncCodeActivity> 派生的活动）或消息活动，则控件制将传递给下一个分支，同时子活动等待其要接收的消息或其要完成的异步工作。  
  
## <a name="flow-control-activities"></a>流控制活动  
  
|Activity|描述|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.DoWhile>|执行所包含的活动一次并在条件为 `true` 时继续执行该操作。|  
|<xref:System.Activities.Statements.ForEach%601>|对集合中的每个元素按顺序执行嵌入的语句。 <xref:System.Activities.Statements.ForEach%601> 与关键字 `foreach` 类似，但它作为活动而非语言语句来实现。|  
|<xref:System.Activities.Statements.If>|如果条件为 `true`，则执行所包含的活动，如果条件为 <xref:System.Activities.Statements.If.Else%2A>，则可以执行 `false` 属性中包含的活动。|  
|<xref:System.Activities.Statements.Parallel>|并行执行所包含的活动。|  
|<xref:System.Activities.Statements.ParallelForEach%601>|对集合中的每个元素并行执行嵌入的语句。|  
|<xref:System.Activities.Statements.Pick>|提供基于事件的控制流建模。|  
|<xref:System.Activities.Statements.PickBranch>|表示 <xref:System.Activities.Statements.Pick> 活动中的可能执行路径。|  
|<xref:System.Activities.Statements.Sequence>|按顺序执行所包含的活动。|  
|<xref:System.Activities.Statements.Switch%601>|基于给定表达式的值，从要执行的多个活动中选择一个活动。|  
|<xref:System.Activities.Statements.While>|条件为 `true` 时执行所包含的活动。|
