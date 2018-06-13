---
title: '&lt;transportConfigurationTypes&gt;'
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 422de17f4c1b42579eadc16c7ec1a0037903d1a9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766947"
---
# <a name="lttransportconfigurationtypesgt"></a>&lt;transportConfigurationTypes&gt;
特定のトランスポートの型を識別する構成要素のコレクションを表します。 これはカスタム WAS プロトコルの追加に使用できます。  
  
 \<system.ServiceModel >  
\<ServiceHostingEnvironment >  
\<transportConfigurationTypes >  
  
## <a name="syntax"></a>構文  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|トランスポートの名前|  
|transportConfigurationType|トランスポートを実装する型|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|特定のトランスポートの型を識別する構成要素を追加します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ServiceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|環境をホストするサービスがインスタンス化する特定のトランスポートの型を定義します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [ホスティング](../../../../../docs/framework/wcf/feature-details/hosting.md)
