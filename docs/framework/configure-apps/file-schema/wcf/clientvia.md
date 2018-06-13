---
title: '&lt;clientVia&gt;'
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 6218bb3f205f2825eb3f10fabf834cfd0396ac87
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754133"
---
# <a name="ltclientviagt"></a>&lt;clientVia&gt;
トランスポート チャネルの作成対象となる URI を指定します。 詳細については、「<xref:System.ServiceModel.Description.ClientViaBehavior>」を参照してください。  
  
 \<system.ServiceModel >  
\<ビヘイビアー >  
\<endpointBehaviors>  
\<behavior>  
\<clientVia >  
  
## <a name="syntax"></a>構文  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`viaUri`|メッセージの経路を示す URI を指定する文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|エンドポイントの動作を指定します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
