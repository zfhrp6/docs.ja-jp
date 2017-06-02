---
title: "WS-I Basic Profile 1.1 の相互運用可能サービスの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "構成 [WCF], 相互運用可能サービス"
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# WS-I Basic Profile 1.1 の相互運用可能サービスの作成
[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Web サービス クライアントと相互運用できるように [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] サービス エンドポイントを構成するには、以下に従います。  
  
-   使用して、 <xref:System.ServiceModel.BasicHttpBinding?displayProperty=fullName>サービス エンドポイントのバインディングの種類として。  
  
-   コールバック コントラクト機能とセッション コントラクト機能の使用、およびトランザクション動作のサービス エンドポイントでの使用をいずれも行わない。  
  
 必要に応じて、HTTPS およびトランスポート レベルのクライアント認証のサポートをバインディングで有効にできます。  
  
 次の機能、 <xref:System.ServiceModel.BasicHttpBinding>クラスは、WS 以外の機能を必要と-基本プロファイル 1.1。  
  
-   によって制御される message Transmission Optimization Mechanism (MTOM) メッセージ エンコーディング、 <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=fullName>プロパティです。 このプロパティは、既定値のままに<xref:System.ServiceModel.WSMessageEncoding?displayProperty=fullName> MTOM を使用しないようにします。  
  
-   によって制御されるメッセージ セキュリティ、 <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=fullName>値に準拠した Ws-security サポートを提供するには Basic Security Profile 1.0 です。 このプロパティは、既定値のままに<xref:System.ServiceModel.SecurityMode?displayProperty=fullName> Ws-security を使用しないようにします。  
  
 メタデータを有効にする、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]に利用できるサービス[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]、Web サービス クライアント生成ツールを使用して: [Web サービス記述言語ツール (Wsdl.exe)](http://msdn.microsoft.com/ja-jp/b9210348-8bc2-4367-8c91-d1a04b403e88)、 [Web サービス検出ツール (Disco.exe)](http://msdn.microsoft.com/ja-jp/acd88078-c581-42bc-94ca-6633e2851979)、および`Add Web Reference`機能[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]; メタデータの公開を有効にする必要があります。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][メタデータ エンドポイントを公開](../../../docs/framework/wcf/publishing-metadata-endpoints.md)します。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Web サービス クライアントと互換性のある [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] エンドポイントをコードおよび構成ファイルで追加する方法を次のコード例に示します。  
  
### <a name="code"></a>コード  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
  
 <!-- TODO: review snippet reference [!code[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/common/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  -->  
  
## <a name="see-also"></a>関連項目  
 [ASP.NET Web サービスとの相互運用性](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)