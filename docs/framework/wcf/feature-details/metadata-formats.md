---
title: "メタデータ形式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b7812023fbe2159daba205727e20e1b69b84686
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="metadata-formats"></a>メタデータ形式
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、次の表に示すメタデータ形式をサポートしています。  
  
## <a name="metadata-specifications-and-usage"></a>メタデータの仕様と用途  
  
|プロトコル|仕様と用途|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web サービス記述言語 (WSDL) 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、サービスの記述に Web サービス記述言語 (WSDL) を使用します。|  
|XML スキーマ|[XML Schema Part 2: Datatypes Second Edition](http://go.microsoft.com/fwlink/?LinkId=94861)と[XML Schema Part 1: Structures Second Edition](http://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、メッセージ内で使用されるデータ型の記述に XML スキーマを使用します。|  
|WS-Policy|[Web サービス ポリシー 1.2 - フレームワーク (Ws-policy)](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [1.5 - Framework web サービス ポリシー](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、ドメイン固有のアサーションと共に WS-Policy 1.2 または 1.5 の仕様を使用して、サービス要件と機能を記述します。|  
|WS-PolicyAttachments|[Web サービス ポリシー 1.2: 添付ファイル (Ws-policyattachment)](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、WSDL のさまざまなスコープにポリシー表現を関連付けるために、WS-PolicyAttachments が実装されています。|  
|WS-Metadata Exchange|[Web サービス メタデータ交換 (Ws-metadataexchange) バージョン 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、XML スキーマ、WSDL、WS-Policy を取得するために WS-MetadataExchange が実装されています。|  
|WS Addressing Binding for WSDL|[Web Services Addressing 1.0 - WSDL バインディング](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、WSDL でアドレス指定情報を関連付けるために、WS-Addressing Binding for WSDL が実装されています。|  
  
## <a name="see-also"></a>参照  
 [システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [WSDL とポリシー](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
