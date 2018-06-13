---
title: '&lt;enableWebScript&gt;'
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: b14923c1b9a80bcd1c47db0e4fad6a6224b95329
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751897"
---
# <a name="ltenablewebscriptgt"></a>&lt;enableWebScript&gt;
この要素は、ASP.NET AJAX Web ページからサービスを使用できるようにするエンドポイントの動作を有効にします。  
  
 \<system.ServiceModel >  
\<ビヘイビアー >  
\<endpointBehaviors>  
\<behavior>  
\<enableWebScript >  
  
## <a name="syntax"></a>構文  
  
```xml  
<enableWebScript />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|エンドポイントの動作のセットを指定します。|  
  
## <a name="remarks"></a>コメント  
 この動作は、いずれかと組み合わせてのみ使用する必要があります、 [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)標準バインディングまたは[ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md)バインド要素。  この動作の詳細については、「<xref:System.ServiceModel.Description.WebScriptEnablingBehavior>」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>  
 [AJAX の統合と JSON のサポート](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [\<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
