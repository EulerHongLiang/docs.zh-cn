---
title: '&lt;certificateReference&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: fd0d4742a162000d438851cef9c00e21368b7ba1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificatereferencegt"></a>&lt;certificateReference&gt;
指定用于查找和验证的证书存储区中的 X.509 证书的设置。  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<serviceCertificate >  
\<certificateReference >  
  
## <a name="syntax"></a>语法  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|storeName|X.509 证书存储区的名称。 默认值为"My"。 可选。|  
|storeLocation|A<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，该值指定 X.509 证书存储区的位置。 默认值为"LocalMachine"。 可选。|  
|x509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType>值，该值指定是要执行的搜索的类型。 默认值为"FindBySubjectDistinguishedName"。 可选。|  
|findValue|要在 X.509 证书存储区中搜索的值。 可选。|  
|isChainIncluded|指定是否应执行验证通过使用证书链。 默认值为"true";通过使用证书链执行验证。 可选。|  
  
### <a name="child-elements"></a>子元素  
 无  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|配置用来加密和解密令牌的证书。|  
  
## <a name="remarks"></a>备注  
 `<certificateReference>`元素指定用于查找和验证的证书存储区中的 X.509 证书的设置。 当指定的子元素为`<serviceCertficate>`元素，它指定用于加密和解密令牌的 X.509 证书的位置和验证设置。 `<certificateReference>`元素表示由<xref:System.ServiceModel.Configuration.CertificateReferenceElement>类。
