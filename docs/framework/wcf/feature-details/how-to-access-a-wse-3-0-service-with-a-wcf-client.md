---
title: '方法 : WCF クライアントで WSE 3.0 サービスにアクセスする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
ms.openlocfilehash: 54d795858b85bd72a01f619b3603c9927df655d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>方法 : WCF クライアントで WSE 3.0 サービスにアクセスする
Windows Communication Foundation (WCF) クライアントは、WCF クライアントが Ws-addressing 仕様の 2004 年 8 月版を使用して構成されている場合、Microsoft .NET サービス用のワイヤレベルの互換性のある Web サービス拡張 (WSE) 3.0 がします。 ただし、WSE 3.0 サービス プロトコルをサポートしない、メタデータ交換 (MEX)、これを使用する場合、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を WCF クライアント クラスを作成するには、セキュリティ設定は適用されませんを生成されました。WCF クライアントです。 そのため、セキュリティの設定を指定する必要があります、WCF クライアントが生成された後に、WSE 3.0 サービスが必要であります。  
  
 これらのセキュリティ設定を適用するには、WSE 3.0 サービスの要件、および WSE 3.0 サービスと WCF クライアントの間で相互運用可能な要件を考慮するカスタム バインディングを使用します。 これらの相互運用性要件には、前述の 2004 年 8 月版 WS-Addressing 仕様の使用と、WSE 3.0 の既定のメッセージ保護が <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> であることが含まれます。 WCF の既定のメッセージ保護は<xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>します。 このトピックでは、WSE 3.0 サービスと相互運用する WCF バインドを作成する方法について説明します。 WCF には、このバインディングが組み込まれたサンプルも用意されています。 このサンプルの詳細については、次を参照してください。 [ASMX Web サービスとの相互運用](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md)です。  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>WCF クライアントで WSE 3.0 サービスにアクセスするには  
  
1.  実行、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WSE 3.0 Web サービスの WCF クライアントを作成します。  
  
     WSE 3.0 Web サービス、WCF クライアントが作成されます。 WSE 3.0 は MEX プロトコルをサポートしていないため、このツールを使用して Web サービスのセキュリティ要件を取得することはできません。 アプリケーション開発者は、クライアントのセキュリティ設定を追加する必要があります。  
  
     WCF クライアントの作成の詳細については、次を参照してください。、[する方法: クライアントを作成する](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。  
  
2.  WSE 3.0 Web サービスと通信できるバインディングを表すクラスを作成します。  
  
     次のクラスの一部である、 [WSE との相互運用](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)サンプル。  
  
    1.  <xref:System.ServiceModel.Channels.Binding> クラスから派生するクラスを作成します。  
  
         `WseHttpBinding` クラスから派生する、<xref:System.ServiceModel.Channels.Binding> という名前のクラスを作成する方法を次のコード例に示します。  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  WSE サービスで使用する WSE 設定不要アサーション、派生キーが必要かどうか、セキュリティで保護されたセッションを使用するかどうか、署名の確認が必要かどうか、およびメッセージ保護設定を指定するプロパティを、このクラスに追加します。 WSE 3.0 では、設定不要アサーションは、クライアントまたは Web サービスのセキュリティ要件を指定します: WCF バインディングの認証モードに似ています。  
  
         WSE 設定不要アサーション、派生キーが必要かどうか、セキュリティで保護されたセッションを使用するかどうか、署名の確認が必要かどうか、およびメッセージ保護設定をそれぞれ指定する、`SecurityAssertion`、`RequireDerivedKeys`、`EstablishSecurityContext`、および `MessageProtectionOrder` の各プロパティを定義するコード例を次に示します。  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> メソッドをオーバーライドして、バインディング プロパティを設定します。  
  
         `SecurityAssertion` プロパティと `MessageProtectionOrder` プロパティの値を取得することで、トランスポート、メッセージ エンコーディング、メッセージ保護設定を指定するコード例を次に示します。  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  クライアントのアプリケーション コードでは、コードを追加してバインディングのプロパティを設定します。  
  
     次のコード例を WCF クライアント必要があります使用するように指定メッセージの保護と認証、WSE 3.0 で定義されている`AnonymousForCertificate`設定不要のセキュリティ アサーションです。 また、セキュリティで保護されたセッションと派生キーが必要です。  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>例  
 WSE 3.0 の設定不要のセキュリティ アサーションのプロパティに対応するプロパティを公開するカスタムのバインディングを定義するコード例を次に示します。 カスタムのバインディングの名前は、 `WseHttpBinding`、WSSecurityAnonymous WSE 3.0 QuickStart のサンプルと通信する WCF クライアントのバインドのプロパティを指定するのには、使用しています。  
  
  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.Binding>  
 [WSE との相互運用](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
