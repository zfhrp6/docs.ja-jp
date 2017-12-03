---
title: "方法 : WCF サービスおよび ASP.NET Web サービス クライアントを相互運用するために構成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ed4bf8e86e727505d48e85bb55a88452217c76b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>方法 : WCF サービスおよび ASP.NET Web サービス クライアントを相互運用するために構成する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web サービス クライアントと相互運用できるように [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] サービス エンドポイントを構成するには、サービス エンドポイントのバインディングの種類として <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> を使用します。  
  
 必要に応じて、HTTPS およびトランスポート レベルのクライアント認証のサポートをバインディングで有効にできます。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web サービス クライアントでは MTOM メッセージ エンコーディングがサポートされていないため、<xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> プロパティは、既定値である <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> のままにしておきます。 また、ASP.Net Web サービス クライアントでは WS-Security がサポートされていないため、<xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> を <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定する必要があります。  
  
 メタデータを行うために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]に利用できるサービス[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web サービス プロキシ生成ツール (つまり、 [Web サービス記述言語ツール (Wsdl.exe)](http://go.microsoft.com/fwlink/?LinkId=73833)、 [Web サービス検出ツール (Disco.exe)](http://go.microsoft.com/fwlink/?LinkId=73834)、および Visual Studio で Web 参照の追加機能)、HTTP GET メタデータ エンドポイントを公開する必要があります。  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>コードを使用して ASP.NET Web サービス クライアントと互換性のある WCF エンドポイントを追加するには  
  
1.  新しい <xref:System.ServiceModel.BasicHttpBinding> インスタンスを作成します。  
  
2.  必要に応じて、バインディングのセキュリティ モードを <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定して、このサービス エンドポイント バインディングのトランスポート セキュリティを有効にします。 詳細については、「[トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security.md)です。  
  
3.  上で作成したバインディング インスタンスを使用して、サービス ホストに新しいアプリケーション エンドポイントを追加します。 コードでサービス エンドポイントを追加する方法の詳細については、次を参照してください。、[する方法: コードでサービス エンドポイントの作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)です。  
  
4.  サービス用に HTTP/GET メタデータのエンドポイントを有効にします。 詳細をご覧ください[する方法: サービスを使用してコードのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)です。  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>構成ファイルを使用して ASP.NET Web サービス クライアントと互換性のある WCF エンドポイントを追加するには  
  
1.  新しい <xref:System.ServiceModel.BasicHttpBinding> バインディング構成を作成します。 詳細については、次を参照してください。、[する方法: 構成では、サービス バインドを指定して](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)です。  
  
2.  必要に応じて、バインディングのセキュリティ モードを <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定して、このサービス エンドポイント バインディング構成のトランスポート セキュリティを有効にします。 詳細については、「[トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security.md)です。  
  
3.  上で作成したバインド構成を使用して、サービスに新しいアプリケーション エンドポイントを構成します。 構成ファイルでサービス エンドポイントを追加する方法の詳細については、次を参照してください。、[する方法: 構成でサービス エンドポイントの作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)です。  
  
4.  サービス用に HTTP/GET メタデータのエンドポイントを有効にします。 詳細を参照してください、[する方法: 構成ファイルを使用して、サービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)です。  
  
## <a name="example"></a>例  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web サービス クライアントと互換性のある [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] エンドポイントをコードおよび構成ファイルで追加する方法を次のコード例に示します。  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)] 
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)] 
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]     
  
## <a name="see-also"></a>関連項目  
 [方法: コードでサービス エンドポイントの作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 [方法: コードを使用して、サービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 [方法: 構成でサービス バインディングを指定する](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [方法: 構成でサービス エンドポイントの作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [方法: 構成ファイルを使用して、サービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [メタデータを使用します。](../../../../docs/framework/wcf/feature-details/using-metadata.md)
