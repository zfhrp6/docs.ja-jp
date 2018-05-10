---
title: WS-I Basic Profile 1.1 の相互運用可能サービスの作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: aa76a6633ef86a908e00bb9dcb1b16eefe35c12d
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>WS-I Basic Profile 1.1 の相互運用可能サービスの作成
相互運用できるようにする WCF サービス エンドポイントを構成する[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]Web サービス クライアント。  
  
-   サービス エンドポイントのバインディングの種類として <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> を使用する。  
  
-   コールバック コントラクト機能とセッション コントラクト機能の使用、およびトランザクション動作のサービス エンドポイントでの使用をいずれも行わない。  
  
 必要に応じて、HTTPS およびトランスポート レベルのクライアント認証のサポートをバインディングで有効にできます。  
  
 <xref:System.ServiceModel.BasicHttpBinding> クラスの次の機能を使用する場合、WS-I Basic Profile 1.1 の機能では十分ではありません。  
  
-   <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> プロパティで制御される MTOM (Message Transmission Optimization Mechanism) メッセージ エンコーディング。 MTOM を使用しない場合は、このプロパティを既定値 (<xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>) のままにしておきます。  
  
-   <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> 値によって制御されるメッセージ セキュリティでは、WS-I Basic Security Profile 1.0 に準拠した WS-Security がサポートされます。 WS-Security を使用しない場合は、このプロパティを既定値 (<xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType>) のままにしておきます。  
  
 WCF サービスのメタデータを使用できるようにする[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]、Web サービス クライアント生成ツールを使用して: [Web サービス記述言語ツール (Wsdl.exe)](http://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88)、 [Web サービス検出ツール (Disco.exe)](http://msdn.microsoft.com/library/acd88078-c581-42bc-94ca-6633e2851979)、および`Add Web Reference`Visual Studio の機能です。 メタデータの公開を有効にする必要があります。 詳細については、次を参照してください。[メタデータ エンドポイントを公開する](../../../docs/framework/wcf/publishing-metadata-endpoints.md)です。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次のコード例と互換性がある WCF エンドポイントを追加する方法を示します[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]Web サービス クライアント コードで、または、構成ファイルにします。  
  
### <a name="code"></a>コード  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>関連項目  
 [ASP.NET Web サービスとの相互運用](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
