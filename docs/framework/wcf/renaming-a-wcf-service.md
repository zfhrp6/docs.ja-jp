---
title: "WCF サービス名の変更"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ee707a898bf915491cc1ca44e0606c261dc87dc6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="renaming-a-wcf-service"></a>WCF サービス名の変更
ここでは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスの名前を変更する方法について説明します。  
  
## <a name="renaming-a-wcf-service"></a>WCF サービス名の変更  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] テンプレートでサービスの名前を変更するには、次の手順を実行します。  
  
-   サービスを実装するクラスの名前を変更します。  
  
-   次の例に示すように、このサービスの構成ファイルで、サービスの名前を新しい名前に変更します。 構成ファイルは、ホスト モデルに応じて、app.config または web.config ファイルのどちらかです。  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   サービスが Web ホストである場合、*.svc ファイルが使用されます。 この svc ファイルを開き、次の例に示すように、サービスの名前を変更します。 自己ホスト アプリケーションには svc ファイルがないので、この手順は必要ありません。  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a>WCF サービス コントラクト名の変更  
  
-   サービス コントラクトの名前を変更するには、次の手順を実行します。  
  
-   サービス コントラクトの名前を変更します。  
  
-   次の例に示すように、このサービスの構成ファイルで、サービス コントラクトの名前を新しい名前に変更します。 構成ファイルは、ホスト モデルに応じて、app.config または web.config ファイルのどちらかです。  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
