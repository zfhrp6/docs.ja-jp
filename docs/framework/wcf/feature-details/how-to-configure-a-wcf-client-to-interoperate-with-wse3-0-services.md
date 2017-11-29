---
title: "方法 : WCF クライアントと WSE3.0 サービスを相互運用するために構成する"
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
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2dbd83de39f7daa96ec5566084e925f878e32154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>方法 : WCF クライアントと WSE3.0 サービスを相互運用するために構成する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアントが WS-Addressing 仕様の 2004 年 8 月版を使用して構成されている場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントは Microsoft .NET サービスの WSE (Web サービス拡張) 3.0 とネットワーク レベルで互換性があります。  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>WSE 3.0 Web サービスと相互運用するように WCF クライアントを構成するには  
  
1.  実行、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を作成する、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSE 3.0 Web サービスのクライアントです。  
  
     WSE Web サービスに対して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント クラスが作成されます。  
  
     作成する方法について、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアントを参照してください、[する方法: クライアントを作成する](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。  
  
2.  WSE 3.0 Web サービスと通信できるバインディングを表すクラスを作成します。  
  
     次のクラスの一部である、 [WSE との相互運用](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41)サンプルです。  
  
    1.  <xref:System.ServiceModel.Channels.Binding> クラスから派生するクラスを作成します。  
  
         `WseHttpBinding` クラスから派生する、<xref:System.ServiceModel.Channels.Binding> という名前のクラスを作成する方法を次のコード例に示します。  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  WSE の設定不要アサーションを指定するクラスに、派生キーが必要か、セキュリティで保護されたセッションが使用されるか、署名の確認が必要かどうかの指定、およびメッセージ保護設定などのプロパティを追加します。  
  
         次のコード例で定義`SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder`WSE 設定不要アサーション、派生キーが必要かどうか、セキュリティで保護されたセッションを使用するかどうか、署名の確認が必要かどうかおよびメッセージ保護設定を指定するプロパティそれぞれします。  
  
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
 WSE 3.0 の設定不要のセキュリティ アサーションのプロパティに対応するプロパティを公開するカスタムのバインディングを定義するコード例を次に示します。 この `WseHttpBinding` という名前のカスタム バインディングを使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントのバインディング プロパティを指定します。  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.Binding>  
 [WSE との相互運用](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41)
