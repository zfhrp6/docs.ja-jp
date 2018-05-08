---
title: メタデータ形式
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: a3c6b1f551d1bff8c68a91f33e62df289d2078cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="metadata-formats"></a>メタデータ形式
Windows Communication Foundation (WCF) では、次の表に、メタデータの形式をサポートしています。  
  
## <a name="metadata-specifications-and-usage"></a>メタデータの仕様と用途  
  
|プロトコル|仕様と用途|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web サービス記述言語 (WSDL) 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> WCF では、Web サービス記述言語 (WSDL) を使用して、サービスについて説明します。|  
|XML スキーマ|[XML Schema Part 2: Datatypes Second Edition](http://go.microsoft.com/fwlink/?LinkId=94861)と[XML Schema Part 1: Structures Second Edition](http://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> WCF では、メッセージで使用されるデータ型を記述するのに XML スキーマを使用します。|  
|WS-Policy|[Web サービス ポリシー 1.2 - フレームワーク (Ws-policy)](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [1.5 - Framework web サービス ポリシー](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> WCF は、Ws-policy 1.2 または 1.5 の仕様とドメイン固有のアサーションをサービス要件と機能について説明します。|  
|WS-PolicyAttachments|[Web サービス ポリシー 1.2: 添付ファイル (Ws-policyattachment)](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> WCF では、WSDL 内のさまざまなスコープでポリシー式をアタッチする Ws-policy の添付ファイルを実装します。|  
|WS-Metadata Exchange|[Web サービス メタデータ交換 (Ws-metadataexchange) バージョン 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF には、XML スキーマ、WSDL、Ws-policy を取得するには、Ws-metadataexchange が実装されています。|  
|WS Addressing Binding for WSDL|[Web Services Addressing 1.0 - WSDL バインディング](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> WCF では、Ws-addressing Binding for WSDL でアドレス指定情報をアタッチする WSDL を実装します。|  
  
## <a name="see-also"></a>関連項目  
 [システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [WSDL とポリシー](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
