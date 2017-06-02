---
title: "方法 : SecurityBindingElement を使用してカスタム バインドを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "セキュリティ [WCF] カスタム バインディングの作成"
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
caps.latest.revision: 19
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 19
---
# 方法 : SecurityBindingElement を使用してカスタム バインドを作成する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] にはシステム指定のバインディングがいくつか含まれています。これらのバインディングは構成できますが、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] がサポートするすべてのセキュリティ オプションを構成しようとする場合には十分な柔軟性が得られません。 ここでは、個別のバインド要素からカスタム バインドを直接作成する方法を説明し、このようなバインディングを作成する場合に指定できるセキュリティ設定のいくつかに焦点を当てます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]カスタム バインディングを作成するを参照してください[バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)します。  
  
> [!WARNING]
>  <xref:System.ServiceModel.Channels.SecurityBindingElement>はサポートしていません、 <xref:System.ServiceModel.Channels.IDuplexSessionChannel>チャネル形状をチャネル形状によって使用される既定の TCP は、トランスポートの場合に<xref:System.ServiceModel.TransferMode>に設定されている<xref:System.ServiceModel.TransferMode.Buffered>します。 設定する必要があります<xref:System.ServiceModel.TransferMode>に<xref:System.ServiceModel.TransferMode.Streamed>を使用するために<xref:System.ServiceModel.Channels.SecurityBindingElement>このシナリオでします。  
  
## <a name="creating-a-custom-binding"></a>カスタム バインドの作成  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]のすべてのバインドが構成されている*バインド要素*します。 派生した各バインド要素、 <xref:System.ServiceModel.Channels.BindingElement>クラスです。 標準のシステム指定のバインディングの場合、バインド要素は自動的に作成および構成されます。ただし、プロパティ設定の一部はカスタマイズが可能です。  
  
 これに対し、カスタム バインディングを作成するバインド要素作成および構成されると、 <xref:System.ServiceModel.Channels.CustomBinding>のバインド要素から作成します。  
  
 これを行うには、インスタンスによって表されるコレクションに個別のバインド要素を追加した、 <xref:System.ServiceModel.Channels.BindingElementCollection>クラス、および設定し、`Elements`のプロパティ、`CustomBinding`そのオブジェクトと等しい。 バインド要素は、トランザクション フロー、信頼できるセッション、セキュリティ、複合二重、一方向、ストリーム セキュリティ、メッセージ エンコーディング、トランスポートの順に追加する必要があります。 どのバインディングでも、これらすべてのバインド要素が必要になるとは限りません。  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  
 次の&3; つのバインド要素から派生できるすべてのメッセージ レベルのセキュリティに関連、 <xref:System.ServiceModel.Channels.SecurityBindingElement>クラスです。 3 つ<xref:System.ServiceModel.Channels.TransportSecurityBindingElement>、 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>、および<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>します。 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>混合モード セキュリティを提供するために使用します。 他の&2; つの要素は、メッセージ層でセキュリティを提供する場合に使用します。  
  
 トランスポート レベルのセキュリティが提供される場合は、次の追加のクラスが使用されます。  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
## <a name="required-binding-elements"></a>必要なバインド要素  
 1 つのバインディングに結合できる可能性のあるバインド要素は多数存在します。 これらの組み合わせすべてが有効なわけではありません。 ここでは、セキュリティ バインディングに存在する必要のある要素について説明します。  
  
 有効なセキュリティ バインディングは、次のような多くの要因に依存します。  
  
-   セキュリティ モード  
  
-   トランスポート プロトコル  
  
-   コントラクトに指定されているメッセージ交換パターン (MEP)  
  
 前述の要因の各組み合わせに有効なバインド要素のスタックの構成を次の表に示します。 これらは最小限の要件であることに注意してください。 メッセージ エンコーディング バインド要素、トランザクション バインド要素などの追加のバインド要素をバインディングに追加することもできます。  
  
|セキュリティ モード|Transport|コントラクトのメッセージ交換パターン|コントラクトのメッセージ交換パターン|コントラクトのメッセージ交換パターン|  
|-------------------|---------------|---------------------------------------|---------------------------------------|---------------------------------------|  
|||`Datagram`|`Request Reply`|`Duplex`|  
|Transport|Https||||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP||||  
|||OneWayBindingElement|||  
|||SSL または Windows StreamSecurityBindingElement|SSL または Windows StreamSecurityBindingElement|SSL または Windows StreamSecurityBindingElement|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|メッセージ|Http|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement (認証モード = SecureConversation)|  
|||||CompositeDuplexBindingElement|  
|||OneWayBindingElement||OneWayBindingElement|  
|||HttpTransportBindingElement|HttpTransportBindingElement|HttpTransportBindingElement|  
||Tcp|SecurityBindingElement|SecurityBindingElement|SymmetricSecurityBindingElement (認証モード = SecureConversation)|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|混合 (メッセージ資格情報付きトランスポート)|Https|TransportSecurityBindingElement|TransportSecurityBindingElement||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP|TransportSecurityBindingElement|SymmetricSecurityBindingElement (認証モード = SecureConversation)|SymmetricSecurityBindingElement (認証モード = SecureConversation)|  
|||OneWayBindingElement|||  
|||SSL または Windows StreamSecurityBindingElement|SSL または Windows StreamSecurityBindingElement|SSL または Windows StreamSecurityBindingElement|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
  
 SecurityBindingElements には構成可能な設定が多数あることに注意してください。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][SecurityBindingElement 認証モード](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)します。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][メッセージ交換とセッションをセキュリティで保護](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)します。  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement を使用するカスタム バインドを作成するには  
  
1.  インスタンスを作成、 <xref:System.ServiceModel.Channels.BindingElementCollection>名前を持つクラス`outputBec`します。  
  
2.  静的メソッドを呼び出して`M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)`のインスタンスを返す、 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>クラスです。  
  
3.  追加、 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>コレクション (`outputBec`) を呼び出して、`Add`のメソッド、<xref:System.Collections.ObjectModel.Collection%601>の<xref:System.ServiceModel.Channels.BindingElement>クラスです。  
  
4.  インスタンスを作成、 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>クラスにし、コレクションに追加 (`outputBec`)。 これにより、バインディングによって使用されるエンコーディングが指定されます。  
  
5.  作成、 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>コレクションに追加し、(`outputBec`)。 これにより、バインディングが HTTP トランスポートを使用することが指定されます。  
  
6.  インスタンスを作成することで、新しいカスタム バインドを作成、 <xref:System.ServiceModel.Channels.CustomBinding>クラスとコレクションを渡す`outputBec`コンス トラクターにします。  
  
7.  作成されたカスタム バインディングは、標準と同じ特性を数多く共有<xref:System.ServiceModel.WSHttpBinding>します。 カスタム バインディングではメッセージ レベルのセキュリティと Windows 資格情報が指定されていますが、セキュリティで保護されたセッションは無効になっているため、サービス資格情報が帯域外で指定される必要があり、また署名も暗号化されません。 最後は設定によってのみ制御できます、 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A>プロパティ手順 4. で示したようにします。 他の&2; つについては、標準バインディングの設定を使用することで制御できます。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例を使用するカスタム バインディングを作成する関数全体を提供する、 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>します。  
  
### <a name="code"></a>コード  
 [!code-csharp[c_CustomBinding#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#20)]
 [!code-vb[c_CustomBinding#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombinding/vb/source.vb#20)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>   
 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>   
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [システム指定のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)