---
title: '&lt;exposedMethod&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9e5c9f61d67850d249d54ed5adfc08bf40bad47
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltexposedmethodgt"></a>&lt;exposedMethod&gt;
COM+ コンポーネントのインターフェイスが Web サービスとして公開されるときに公開される COM+ メソッドを表します。  
  
 \<システムです。ServiceModel >  
\<comContracts >  
\<comContract >  
\<メソッド >  
  
## <a name="syntax"></a>構文  
  
```xml  
<comContracts>  
  <comContract>  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|COM+ コンポーネントのインターフェイスが Web サービスとして公開されるときに公開される COM+ メソッドを含む文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<exposedMethods >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|コレクション[ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)要素。|  
  
## <a name="remarks"></a>コメント  
 COM+ 統合構成ツール (ComSvcConfig.exe) を使用して、COM インターフェイスから特定のメソッドを追加して、生成されるサービス コントラクトに表示できます。  
  
 たとえば、次のコマンドを使用して、`IFinances`.Financial コンポーネントの `ItemOrders` COM インターフェイスから、3 つの名前付きメソッドを、生成されるサービス コントラクトに追加できます。  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 また、ComSvcConfig.exe を実行するときとして前述のメソッドを一覧表示する次のサービス コントラクトが生成されます[ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)要素。  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" name="IFinances" namespace="http://contoso.com/services/financial">  
    <exposedMethod name="TransferFunds"/>  
    <exposedMethod name="AddFunds"/>  
    <exposedMethod name="RemoveFunds"/>  
</comContract>  
```  
  
 サービスの初期化時に、ランタイムを反映しての一覧に含まれるメソッドのみを追加するサービス コントラクトの生成を試みます[ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)要素。 トレースは、サービス コントラクトに含まれないインターフェイス メソッド用に作成されます。  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Configuration.ComMethodElementCollection>  
 <xref:System.ServiceModel.Configuration.ComMethodElement>  
 [\<comContracts >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [COM+ アプリケーションとの統合](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [方法 : COM+ サービス設定を構成する](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
