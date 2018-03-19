---
title: '&lt;comContracts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69fbce3f312833c374a4c2615a15359d9c2db3a7
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="ltcomcontractsgt"></a>&lt;comContracts&gt;
`comContracts` 構成セクションには、COM+ 統合サービス コントラクトのさまざまなプロパティを指定できる要素が含まれます。  
  
## <a name="specifying-namespace-and-contract"></a>名前空間およびコントラクトの指定  
 COM + 統合サービス コントラクトは現在に制限されて、"http://tempuri.org"名前空間、およびコントラクト名がサポートする COM インターフェイスから派生します。 ただし、構成ファイルの `comContracts` セクションを使用して候補を指定することができます。  
  
 たとえば、次の構成を使用して、サービス コントラクトの名前空間とコントラクト名、およびセッションの多いバインディングで使用させるオプションを指定できます。  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
  </comContract>  
</comContracts>  
```  
  
 サービスが初期化される場合、指定した名前空間およびコントラクト名が、生成されるサービスの説明に適用されます。  
  
 このセクションが空の場合、サービスの初期化によって、サポートしている COM インターフェイス ID から取得された既定の名前空間およびコントラクト名が適用されます。  
  
 さらに、使用することができます、 [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) COM + コンポーネントのインターフェイスが Web サービスとして公開されるときに公開される COM + メソッドを指定する要素。 使用することも、 [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)統合で使用される永続化できる型を指定します。 最後に、使用することができます、 [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)に含めるユーザー定義型 (UDT) をサービス コントラクトに含まれる要素です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [\<comContract>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [COM+ アプリケーションとの統合](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [方法 : COM+ サービス設定を構成する](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
