---
title: 如何：验证 DBML 和外部映射文件
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 4d3fc297078c9f6c1ac8b2d8a498050f294a5437
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>如何：验证 DBML 和外部映射文件
您修改的外部映射文件和 .dbml 文件必须通过其各自架构定义的验证。 本主题提供的步骤的 Visual Studio 用户来实现验证过程。  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a>验证 .dbml 或 XML 文件  
  
1.  在 Visual Studio**文件**菜单上，指向**打开**，然后单击**文件**。  
  
2.  在**打开的文件**对话框框中，单击.dbml 或你想要验证的 XML 映射文件。  
  
     在打开该文件**XML 编辑器**。  
  
3.  右键单击窗口，并依次**属性**。  
  
4.  在**属性**窗口中，单击省略号**架构**属性。  
  
     **XML 架构**对话框随即打开。  
  
5.  请注意符合您需要的相应架构定义。  
  
    -   DbmlSchema.xsd 是用于验证 .dbml 文件的架构定义。 有关详细信息，请参阅[LINQ to SQL 中的代码生成](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)。  
  
    -   LinqToSqlMapping.xsd 是用于验证外部 XML 映射文件的架构定义。 有关详细信息，请参阅[外部映射](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)。  
  
6.  在**使用**列所需的架构定义行，单击打开下拉列表框中，然后单击**使用此架构**。  
  
     此架构定义文件现在即与您的 DBML 或 XML 映射文件关联。  
  
     请确保未选择其他架构定义。  
  
7.  上**视图**菜单上，单击**错误列表**。  
  
     确定是否已生成了错误、警告或消息。 如果未生成，则说明此 XML 文件对此架构定义有效。  
  
## <a name="alternate-method-for-supplying-schema-definition"></a>提供架构定义的另一种方法  
 如果因某种原因导致相应的.xsd 文件未出现在**XML 架构**对话框中，你可以从帮助主题中下载此.xsd 文件。 以下步骤帮助你在所需由 Visual Studio XML 编辑器中的 Unicode 格式保存下载的文件。  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>从帮助主题中复制架构定义文件  
  
1.  找到包含本主题前面部分所述架构定义的帮助主题。  
  
    -   对于.dbml 文件，请参阅[LINQ to SQL 中的代码生成](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)。  
  
    -   对于外部映射文件，请参阅[外部映射](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)。  
  
2.  单击**复制代码**将代码文件复制到剪贴板。  
  
3.  启动记事本以创建一个新文件。  
  
4.  将剪贴板中的代码粘贴到记事本文件中。  
  
5.  在记事本**文件**菜单上，单击**另存为**。  
  
6.  在**编码**框中，选择**Unicode**。  
  
    > [!IMPORTANT]
    >  这样选择可保证在此文本文件前面加上 Unicode 16 字节顺序标记 (`FFFE`)。  
  
7.  在**文件名**框中，创建带.xsd 扩展名的文件名称。  
  
## <a name="see-also"></a>请参阅  
 [参考](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
