---
title: 如何：使用 ResourceDictionary 来管理可本地化的字符串资源
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resources [WPF], packaging string resources
- packaging string resources [WPF]
- ResourceDictionary [WPF]
- localization [WPF], packaging string resources
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 70f8f02f315580c8056ee698b5e45b1a31a3dc74
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>如何：使用 ResourceDictionary 来管理可本地化的字符串资源
此示例演示如何使用<xref:System.Windows.ResourceDictionary>到 Windows Presentation Foundation (WPF) 应用程序的包可本地化的字符串资源。  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>使用 ResourceDictionary 来管理可本地化的字符串资源  
  
1.  创建<xref:System.Windows.ResourceDictionary>，其中包含你想要本地化的字符串。 以下代码显示一个示例。  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     此代码定义字符串资源， `localizedMessage`，类型的<xref:System.String>，从<xref:System>mscorlib.dll 中的命名空间。  
  
2.  添加<xref:System.Windows.ResourceDictionary>到你的应用程序，使用下面的代码。  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  使用字符串资源标记，使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]类似于以下。  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  通过如下所示的代码来使用代码隐藏文件中的字符串资源。  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  对应用程序进行本地化。 有关详细信息，请参阅[本地化应用程序](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)。
