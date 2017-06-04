---
title: "&lt;exposedMethod&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;exposedMethod&gt;
COM\+ コンポーネントのインターフェイスが Web サービスとして公開されるときに公開される COM\+ メソッドを表します。  
  
## 構文  
  
```  
  
<comContracts>  
  <comContract>  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|name|COM\+ コンポーネントのインターフェイスが Web サービスとして公開されるときに公開される COM\+ メソッドを含む文字列。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<exposedMethods\>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|[\<exposedMethod\>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) 要素のコレクション。|  
  
## 解説  
 COM\+ 統合構成ツール \(ComSvcConfig.exe\) を使用して、COM インターフェイスから特定のメソッドを追加して、生成されるサービス コントラクトに表示できます。  
  
 たとえば、次のコマンドを使用して、`ItemOrders`.Financial コンポーネントの `IFinances` COM インターフェイスから、3 つの名前付きメソッドを、生成されるサービス コントラクトに追加できます。  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 ComSvcConfig.exe も実行する場合、前述のメソッドを [\<exposedMethod\>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) 要素として一覧表示する次のサービス コントラクトを生成します。  
  
```  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" name="IFinances" namespace="http://contoso.com/services/financial">  
    <exposedMethod name="TransferFunds"/>  
    <exposedMethod name="AddFunds"/>  
    <exposedMethod name="RemoveFunds"/>  
</comContract>  
```  
  
 サービスの初期化時に、ランタイムは、サービス コントラクトを生成しますが、このとき [\<exposedMethod\>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) 要素の一覧に含まれるメソッドのみを反映して追加しようとします。  トレースは、サービス コントラクトに含まれないインターフェイス メソッド用に作成されます。  
  
## 参照  
 <xref:System.ServiceModel.Configuration.ComMethodElementCollection>   
 <xref:System.ServiceModel.Configuration.ComMethodElement>   
 [\<comContracts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)   
 [COM\+ アプリケーションとの統合](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)   
 [方法 : COM\+ サービス設定を構成する](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)