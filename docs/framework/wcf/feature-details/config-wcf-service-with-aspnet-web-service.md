---
title: "方法 : WCF サービスおよび ASP.NET Web サービス クライアントを相互運用するために構成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# 方法 : WCF サービスおよび ASP.NET Web サービス クライアントを相互運用するために構成する
構成する、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]と相互運用できるようにするサービス エンドポイント[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web サービス クライアントを使用して、 <xref:System.ServiceModel.BasicHttpBinding?displayProperty=fullName>サービス エンドポイントのバインディングの種類として。  
  
 必要に応じて、HTTPS およびトランスポート レベルのクライアント認証のサポートをバインディングで有効にできます。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web サービス クライアントは MTOM メッセージ エンコーディングをサポートしていないため、 <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=fullName>プロパティは、既定値は、これは残しておく必要が<xref:System.ServiceModel.WSMessageEncoding?displayProperty=fullName>します。 ASP.Net Web サービス クライアントは、Ws-security をサポートしていないため、 <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=fullName>に設定する必要があります<xref:System.ServiceModel.BasicHttpSecurityMode>します。  
  
 メタデータを有効にする、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]に利用できるサービス[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web サービス プロキシ生成ツール (つまり、 [Web サービス記述言語ツール (Wsdl.exe)](http://go.microsoft.com/fwlink/?LinkId=73833)、 [Web サービス検出ツール (Disco.exe)](http://go.microsoft.com/fwlink/?LinkId=73834)、および Visual Studio で Web 参照の追加機能)、HTTP GET メタデータ エンドポイントを公開する必要があります。  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>コードを使用して ASP.NET Web サービス クライアントと互換性のある WCF エンドポイントを追加するには  
  
1.  新しい<xref:System.ServiceModel.BasicHttpBinding>インスタンス  
  
2.  必要に応じてこのサービス エンドポイント バインディングのトランスポート セキュリティを有効にするバインディングのセキュリティ モードを設定して<xref:System.ServiceModel.BasicHttpSecurityMode>します。 詳細については、「[トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security.md)します。  
  
3.  上で作成したバインディング インスタンスを使用して、サービス ホストに新しいアプリケーション エンドポイントを追加します。 コードでサービス エンドポイントを追加する方法の詳細については、「、[方法: コードでサービス エンドポイントを作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)します。  
  
4.  サービス用に HTTP/GET メタデータのエンドポイントを有効にします。 詳細をご覧ください[方法: サービスを使用してコードのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)します。  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>構成ファイルを使用して ASP.NET Web サービス クライアントと互換性のある WCF エンドポイントを追加するには  
  
1.  新しい<xref:System.ServiceModel.BasicHttpBinding>バインド構成します。 詳細については、「、[方法: 構成では、サービス バインドを指定](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)します。  
  
2.  必要に応じてこのサービス エンドポイントのバインディング構成のトランスポート セキュリティを有効にするバインディングのセキュリティ モードを設定して<xref:System.ServiceModel.BasicHttpSecurityMode>します。 詳細については、「[トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security.md)します。  
  
3.  上で作成したバインド構成を使用して、サービスに新しいアプリケーション エンドポイントを構成します。 構成ファイルでサービス エンドポイントを追加する方法の詳細については、「、[方法: 構成でサービス エンドポイントを作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)します。  
  
4.  サービス用に HTTP/GET メタデータのエンドポイントを有効にします。 詳細情報を参照してください、[方法: 構成ファイルを使用して、サービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)します。  
  
## <a name="example"></a>例  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web サービス クライアントと互換性のある [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] エンドポイントをコードおよび構成ファイルで追加する方法を次のコード例に示します。  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
  
 <!-- TODO: review snippet reference [!code[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  -->  
  
## <a name="see-also"></a>関連項目  
 [方法: コードでサービス エンドポイントの作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)   
 [方法: コードを使用して、サービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)   
 [方法: 構成でサービス バインディングを指定](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)   
 [方法: 構成でサービス エンドポイントの作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)   
 [方法: 構成ファイルを使用して、サービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)   
 [トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security.md)   
 [メタデータを使用します。](../../../../docs/framework/wcf/feature-details/using-metadata.md)