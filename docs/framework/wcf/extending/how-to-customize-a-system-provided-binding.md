---
title: '方法 : システム指定のバインディングをカスタマイズする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: 04b81689d7d625d519a0a9fc8b1fa6df3df16ada
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803673"
---
# <a name="how-to-customize-a-system-provided-binding"></a>方法 : システム指定のバインディングをカスタマイズする
Windows Communication Foundation (WCF) には、すべてのプロパティでは、基になるバインド要素のプロパティの一部を構成することのいくつかのシステム指定のバインディングが含まれています。 ここでは、バインド要素のプロパティを設定してカスタム バインドを作成する方法を示します。  
  
 直接作成し、システム指定のバインディングを使用せずにバインディング要素を構成する方法の詳細については、次を参照してください。[カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)です。  
  
 作成して、カスタム バインディングの拡張の詳細については、次を参照してください。[バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)です。  
  
 WCF でのすべてのバインディングで構成されて*バインド要素*です。 各バインド要素は <xref:System.ServiceModel.Channels.BindingElement> クラスから派生します。 <xref:System.ServiceModel.BasicHttpBinding> などのシステム指定のバインディングでは、独自のバインド要素が作成され構成されます。 ここでは、バインディングに直接公開されないこのバインド要素 (具体的には <xref:System.ServiceModel.BasicHttpBinding> クラス) のプロパティにアクセスして変更する方法を示します。  
  
 個別のバインド要素は <xref:System.ServiceModel.Channels.BindingElementCollection> クラスで表されるコレクションに格納し、トランザクション フロー、信頼できるセッション、セキュリティ、複合二重、一方向、ストリーム セキュリティ、メッセージ エンコーディング、トランスポートの順に追加します。 どのバインディングでも、これらすべてのバインド要素が必要になるとは限りません。 ユーザー定義のバインド要素も、このバインド要素のコレクションに表示されますが、前述の順序で表示される必要があります。 たとえば、ユーザー定義のトランスポートは、バインド要素コレクションの最後の要素となる必要があります。  
  
 <xref:System.ServiceModel.BasicHttpBinding> クラスには、次の 3 つのバインド要素が含まれています。  
  
1.  オプションのセキュリティ バインド要素。HTTP トランスポートで使用される <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> クラス (メッセージ レベル セキュリティ)、またはトランスポート層がセキュリティを提供する場合 (HTTPS トランスポート) に使用される <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>。  
  
2.  必須のメッセージ エンコーダー バインド要素。<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> または <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>。  
  
3.  必須のトランスポート バインド要素。<xref:System.ServiceModel.Channels.HttpTransportBindingElement> または <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>。  
  
 この例で バインドのインスタンスを作成、生成お、*カスタム バインド*、そこから、カスタム バインディング内のバインド要素を確認し、設定、HTTP バインド要素が見つかったときにその`KeepAliveEnabled`プロパティを`false`. `KeepAliveEnabled` プロパティは、`BasicHttpBinding` に直接公開されていないので、カスタム バインディングを作成し、バインド要素まで移動して、このプロパティを設定する必要があります。  
  
### <a name="to-modify-a-system-provided-binding"></a>システム標準のバインディングを変更するには  
  
1.  <xref:System.ServiceModel.BasicHttpBinding> クラスのインスタンスを作成し、そのセキュリティ モードをメッセージ レベルに設定します。  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  バインディングからカスタム バインディングを作成し、そのカスタム バインディングのプロパティの 1 つから <xref:System.ServiceModel.Channels.BindingElementCollection> クラスを作成します。  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  <xref:System.ServiceModel.Channels.BindingElementCollection> クラスをループして <xref:System.ServiceModel.Channels.HttpTransportBindingElement> クラスが見つかったら、その <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> プロパティを `false` に設定します。  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)
