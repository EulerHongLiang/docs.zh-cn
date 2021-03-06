---
title: 如何：将元数据导入服务终结点
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b86f31217812767b0fbbd785a0f3ff96c2948854
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-import-metadata-into-service-endpoints"></a>如何：将元数据导入服务终结点
本主题说明如何将元数据导入到服务终结点的集合和使用中定义的服务[入门](../../../../docs/framework/wcf/samples/getting-started-sample.md)。 本主题演示如何创建从服务中导入元数据的客户端应用程序，以及之后如何对该服务调用 `Add` 方法。  
  
### <a name="to-import-metadata-into-service-endpoints"></a>将元数据导入服务终结点  
  
1.  声明 <xref:System.ServiceModel.EndpointAddress> 对象，并使用服务的元数据交换 (MEX) 地址的统一资源标识符 (URI) 对其进行初始化。  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2.  创建 <xref:System.ServiceModel.Description.MetadataExchangeClient>、传入 MEX 地址并调用 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>。 此操作将从服务中检索元数据。  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3.  创建 <xref:System.ServiceModel.Description.WsdlImporter>、传入先前检索的元数据并调用 <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>。 此操作将生成 <xref:System.ServiceModel.Description.ContractDescription> 对象的集合。 您还可以根据需要调用 <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> 或 <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>。  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    >  导入元数据后，将无法创建客户端通道或导出元数据。 这是因为此时没有可用的类型信息。 在实际与服务进行交互或导出元数据时需要类型信息。 若要生成类型信息，需要生成代码，如步骤 4 和 5 所示。 或者可以使用 <xref:System.ServiceModel.Description.MetadataResolver> 帮助器类。 有关详细信息，请参阅[如何： 使用 MetadataResolver 动态获取绑定元数据到](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)。  
  
4.  为每个协定生成类型信息。  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5.  现在，您可以使用此信息。 下面的示例生成 C# 源代码。  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a>请参阅  
 [元数据](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [入门](../../../../docs/framework/wcf/samples/getting-started-sample.md)
