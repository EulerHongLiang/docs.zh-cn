---
title: 属性设计
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6dcb164daea6809f0d0e9c221f182d5019385bc1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
---
# <a name="property-design"></a>属性设计
虽然从技术上讲非常类似于方法属性，但它们是在其使用情况方面有很大差异。 它们应被视为智能字段。 它们具有字段，调用语法和方法的灵活性。  
  
 **✓ 执行**创建仅限 get 的属性，如果调用方应不能更改属性的值。  
  
 请记住，如果类型的属性是可变的引用类型，可以更改属性值，即使该属性是只 get。  
  
 **X 不**仅属性的 setter 具有更广泛的可访问性比 getter 提供。  
  
 例如，请使用公共 setter 和受保护的 getter 使用属性。  
  
 如果不能提供属性 getter，请改为实现作为一种方法的功能。 请考虑启动的方法名`Set`并在后面加什么您将已命名属性。 例如，<xref:System.AppDomain>具有一个方法`SetCachePath`而不是让一个名为仅属性`CachePath`。  
  
 **✓ 执行**提供的所有属性，确保，默认值不会导致安全漏洞或您对此低效代码的意义的默认值。  
  
 **✓ 执行**允许将属性按任何顺序设置，即使这会导致临时无效状态的对象。  
  
 它是常见的两个或多个要到其中一个属性的某些值也可能是无效的点又彼此相关的属性对同一个对象提供的其他属性的值。 在这种情况下，从无效的状态导致的异常应会推迟，直到又彼此相关的属性实际一起使用的对象。  
  
 **✓ 执行**保留以前的值，如果属性 setter 将引发异常。  
  
 **请避免 x**属性 getter 从引发异常。  
  
 属性 getter 应该是简单的操作，并且不应具有任何前置条件。 如果 getter 可能会引发异常，它应可能重新设计是一种方法。 请注意，此规则不适用于索引器，我们执行预期异常导致验证自变量的位置。  
  
### <a name="indexed-property-design"></a>索引的属性设计  
 索引的属性是一个特殊属性，可以具有的参数，并且可以使用类似于数组索引的特殊语法调用。  
  
 索引的属性通常称为索引器。 应仅在提供对逻辑集合中的项的访问的 Api 中使用索引器。 例如，一个字符串是字符和上的索引器的集合<xref:System.String?displayProperty=nameWithType>添加了来访问它的字符。  
  
 **请考虑 ✓**使用索引器以提供对存储在内部数组中的数据访问。  
  
 **请考虑 ✓**提供索引器上表示的项的集合的类型。  
  
 **请避免 x**使用索引与多个参数的属性。  
  
 如果设计需要多个参数，请重新考虑是否属性确实表示一个访问器对逻辑集合。 如果不存在，请改为使用方法。 请考虑启动的方法名`Get`或`Set`。  
  
 **请避免 x**具有以外的其他参数类型的索引器<xref:System.Int32?displayProperty=nameWithType>， <xref:System.Int64?displayProperty=nameWithType>， <xref:System.String?displayProperty=nameWithType>， <xref:System.Object?displayProperty=nameWithType>，或枚举。  
  
 如果设计需要其他类型的参数，强重新评估是否 API 确实表示一个访问器对逻辑集合。 如果不存在，请使用方法。 请考虑启动的方法名`Get`或`Set`。  
  
 **✓ 执行**使用名称`Item`的索引属性，除非有显然更好的名称 (例如，请参阅<xref:System.String.Chars%2A>属性`System.String`)。  
  
 在 C# 中，索引器在默认情况下都将名为项。 <xref:System.Runtime.CompilerServices.IndexerNameAttribute>可以用于自定义此名称。  
  
 **X 不**提供索引器和在语义上等效的方法。  
  
 **X 不**提供多个系列中一种类型的重载索引器。  
  
 这是由 C# 编译器实施的。  
  
 **X 不**使用非默认索引属性。  
  
 这是由 C# 编译器实施的。  
  
### <a name="property-change-notification-events"></a>属性更改通知事件  
 有时很有用提供通知中的属性值的更改的用户的事件。 例如，`System.Windows.Forms.Control`引发`TextChanged`后的值的事件其`Text`属性已更改。  
  
 **请考虑 ✓**引发更改通知事件修改高级 Api （通常是设计器组件） 中的属性值时。  
  
 如果没有一种情况最用户知道当更改对象的属性，该对象应引发更改通知事件的属性。  
  
 但是，很可能是值得的开销，若要此类事件针对低级别 Api，如基类型或集合。 例如，<xref:System.Collections.Generic.List%601>不会引发一个新项添加到列表时，此类事件和`Count`属性更改。  
  
 **请考虑 ✓**引发更改通知事件的属性的值更改通过外部强制时。  
  
 如果属性值更改通过某种外部因素 （以通过在对象上调用方法以外的其他方式），则引发事件指示向开发人员值正在更改和已更改。 一个很好示例是`Text`文本框控件的属性。 当用户输入中的文本`TextBox`，会自动更改的属性值。  
  
 *部分 © 2005年，2009 Microsoft Corporation。保留所有权利。*  
  
 *通过从皮尔逊教育版，Inc.的权限重新打印[Framework 设计准则： 约定、 语法和可重用.NET 库，版本 2 的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)通过 Krzysztof Cwalina 和 Brad Abrams，发布 2008 年 10 月 22，通过Microsoft Windows 开发系列的一部分的 Addison Wesley Professional。*  
  
## <a name="see-also"></a>请参阅  
 [成员设计准则](../../../docs/standard/design-guidelines/member.md)  
 [框架设计指南](../../../docs/standard/design-guidelines/index.md)
