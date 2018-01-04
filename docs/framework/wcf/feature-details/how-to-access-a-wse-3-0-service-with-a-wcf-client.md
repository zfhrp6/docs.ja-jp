---
title: "方法 : WCF クライアントで WSE 3.0 サービスにアクセスする"
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
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c70b7df47cb3f367318fb388ceda2163f538cb32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>方法 : WCF クライアントで WSE 3.0 サービスにアクセスする
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアントが WS-Addressing 仕様の 2004 年 8 月版を使用するように構成されている場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントは Microsoft .NET サービスの Web サービス拡張 (WSE: Web Services Enhancements) 3.0 とネットワーク レベルの互換性があります。 ただし、WSE 3.0 サービス プロトコルをサポートしない、メタデータ交換 (MEX)、これを使用する場合、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を作成する、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアント クラスをセキュリティの設定は適用されません生成された[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアント。 そのため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントの生成後に、WSE 3.0 サービスで必要なセキュリティ設定を指定する必要があります。  
  
 カスタム バインディングを使用してこれらのセキュリティ設定を適用することにより、WSE 3.0 サービスの要件、および WSE 3.0 サービスと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントとの相互運用性の要件を考慮に入れることができます。 これらの相互運用性要件には、前述の 2004 年 8 月版 WS-Addressing 仕様の使用と、WSE 3.0 の既定のメッセージ保護が <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> であることが含まれます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の既定のメッセージ保護は、<xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> です。 このトピックでは、WSE 3.0 サービスと相互運用する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] バインディングの作成方法について詳しく説明します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、このバインディングが組み込まれたサンプルも用意されています。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]このサンプルを参照してください[ASMX Web サービスとの相互運用](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md)です。  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>WCF クライアントで WSE 3.0 サービスにアクセスするには  
  
1.  実行、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を作成する、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSE 3.0 Web サービスのクライアントです。  
  
     WSE 3.0 Web サービスに対して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントが作成されます。 WSE 3.0 は MEX プロトコルをサポートしていないため、このツールを使用して Web サービスのセキュリティ要件を取得することはできません。 アプリケーション開発者は、クライアントのセキュリティ設定を追加する必要があります。  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]作成する、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアントを参照してください、[する方法: クライアントを作成する](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。  
  
2.  WSE 3.0 Web サービスと通信できるバインディングを表すクラスを作成します。  
  
     次のクラスの一部である、 [WSE との相互運用](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41)サンプル。  
  
    1.  <xref:System.ServiceModel.Channels.Binding> クラスから派生するクラスを作成します。  
  
         `WseHttpBinding` クラスから派生する、<xref:System.ServiceModel.Channels.Binding> という名前のクラスを作成する方法を次のコード例に示します。  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  WSE サービスで使用する WSE 設定不要アサーション、派生キーが必要かどうか、セキュリティで保護されたセッションを使用するかどうか、署名の確認が必要かどうか、およびメッセージ保護設定を指定するプロパティを、このクラスに追加します。 WSE 3.0 では、設定不要アサーションはクライアントまたは Web サービスのセキュリティ要件を指定します。これらのセキュリティ要件は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のバインディングの認証モードに似ています。  
  
         WSE 設定不要アサーション、派生キーが必要かどうか、セキュリティで保護されたセッションを使用するかどうか、署名の確認が必要かどうか、およびメッセージ保護設定をそれぞれ指定する、`SecurityAssertion`、`RequireDerivedKeys`、`EstablishSecurityContext`、および `MessageProtectionOrder` の各プロパティを定義するコード例を次に示します。  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> メソッドをオーバーライドして、バインディング プロパティを設定します。  
  
         `SecurityAssertion` プロパティと `MessageProtectionOrder` プロパティの値を取得することで、トランスポート、メッセージ エンコーディング、メッセージ保護設定を指定するコード例を次に示します。  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  クライアントのアプリケーション コードでは、コードを追加してバインディングのプロパティを設定します。  
  
     WSE 3.0 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の設定不要なセキュリティ アサーションで定義されているように、メッセージの保護と認証を使用しなければならない `AnonymousForCertificate` クライアントを指定するコード例を次に示します。 また、セキュリティで保護されたセッションと派生キーが必要です。  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>例  
 WSE 3.0 の設定不要のセキュリティ アサーションのプロパティに対応するプロパティを公開するカスタムのバインディングを定義するコード例を次に示します。 この `WseHttpBinding` という名前のカスタムのバインディングは、WSSecurityAnonymous WSE 3.0 QuickStart のサンプルと通信する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントのバインディング プロパティの指定に使用されます。  
  
  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Channels.Binding>  
 [WSE との相互運用](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41)
