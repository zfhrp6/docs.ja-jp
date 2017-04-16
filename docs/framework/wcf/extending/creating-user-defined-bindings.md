---
title: "ユーザー定義バインディングの作成 | Microsoft Docs"
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
  - "ユーザー定義バインディング [WCF]"
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# ユーザー定義バインディングの作成
システムから提供されないバインディングを作成する方法はいくつかあります。  
  
-   バインド要素を格納するコンテナーである <xref:System.ServiceModel.Channels.CustomBinding> クラスに基づいてカスタム バインディングを作成します。  次に、カスタム バインディングをサービス エンドポイントに追加します。  カスタム バインディングは、プログラムで作成することも、アプリケーションの構成ファイルに作成することもできます。  アプリケーション構成ファイルのバインド要素を使用するには、バインド要素で <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> を拡張する必要があります。  カスタム バインディング[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)」および「<xref:System.ServiceModel.Channels.CustomBinding>」を参照してください。  
  
-   標準バインディングの派生クラスを作成できます。  たとえば、<xref:System.ServiceModel.WSHttpBinding> の派生クラスを作成して <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> メソッドを上書きし、バインド要素を取得してカスタム バインディングを挿入したり、セキュリティ用の特定の値を確立したりできます。  
  
-   新しい <xref:System.ServiceModel.Channels.Binding> 型を作成して、バインディング実装全体を完全に制御することができます。  
  
## バインド要素の順序  
 各バインド要素は、メッセージの送信または受信時の処理手順を表します。  実行時に、バインド要素により、送受信チャネル スタックの作成に必要なチャネルとリスナーが作成されます。  
  
 バインディング要素には主に、プロトコル バインディング要素、エンコーディング バインディング要素、トランスポート バインディング要素という 3 つの種類があります。  
  
 プロトコル バインド要素 : この要素はメッセージで動作する上位処理ステップを表します。  このバインド要素で作成したチャネルとリスナーを使って、メッセージ内容の追加、削除、変更が可能です。  特定のバインディングには、それぞれが <xref:System.ServiceModel.Channels.BindingElement> を継承する任意の数のプロトコル バインド要素を含めることができます。  [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] には、<xref:System.ServiceModel.Channels.ReliableSessionBindingElement> や <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> などのプロトコル バインド要素がいくつか含まれます。  
  
 エンコーディング バインド要素 : この要素は、メッセージとネットワーク転送が可能なエンコーディングとの間の変換を表します。  一般的な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] バインディングには、エンコーディング バインド要素が 1 つだけ含まれます。  エンコーディング バインド要素の例として、<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>、<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>、<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> などがあります。  エンコーディング バインド要素がバインディングに指定されていない場合、既定のエンコーディングが使用されます。  既定値は、トランスポートが HTTP の場合はテキスト、それ以外の場合はバイナリです。  
  
 トランスポート バインド要素 : この要素は、トランスポート プロトコルでのエンコーディング メッセージの送信を表します。  一般的な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] バインディングには、<xref:System.ServiceModel.Channels.TransportBindingElement> から派生したトランスポート バインド要素が 1 つだけ含まれます。  トランスポート バインド要素の例として、<xref:System.ServiceModel.Channels.TcpTransportBindingElement>、<xref:System.ServiceModel.Channels.HttpTransportBindingElement>、<xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> などがあります。  
  
 新しいバインディングを作成する場合、バインド要素の追加順序が重要になります。  バインド要素は必ず次の順序で追加します。  
  
|レイヤー|オプション|必須|  
|----------|-----------|--------|  
|トランザクション フロー|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=fullName>|Ｘ|  
|信頼性|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=fullName>|Ｘ|  
|セキュリティ|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=fullName>|Ｘ|  
|複合二重|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=fullName>|Ｘ|  
|エンコーディング|テキスト、バイナリ、MTOM、カスタム|○\*|  
|Transport|TCP、名前付きパイプ、HTTP、HTTPS、MSMQ、およびカスタム|はい|  
  
 \*エンコーディングは各バインディングに必要であるため、エンコーディングが指定されていない場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は既定のエンコーディングを自動的に追加します。  既定値は、HTTP および HTTPS トランスポートの場合はテキスト\/XML、それ以外の場合はバイナリです。  
  
## 新しいバインド要素の作成  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が提供する <xref:System.ServiceModel.Channels.BindingElement> から派生した型のほかに、独自のバインド要素を作成できます。  これにより、他のシステムが提供する型を使ってスタックに組み込むことのできる独自の <xref:System.ServiceModel.Channels.BindingElement> を作成して、バインディングのスタックを作成する方法や、バインディングのスタックに追加するコンポーネントをカスタマイズできます。  
  
 たとえば、メッセージをデータベースに記録する機能を持つ `LoggingBindingElement` を実装する場合、それをチャネル スタックのトランスポート チャネルの上に配置する必要があります。  この場合、アプリケーションでは、次の例に示すように、`TcpTransportBindingElement` と共に `LoggingBindingElement` が組み込まれたカスタム バインディングが作成されます。  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),   
  new TcpTransportBindingElement()  
);  
```  
  
 新しいバインド要素を記述する方法は、機能性の詳細によって異なります。  サンプルの 1 つ \([トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)\) を使用して、1 つの種類のバインド要素の実装方法を詳細に説明します。  
  
## 新しいバインディングの作成  
 ユーザーが作成するバインド要素は、2 つの方法で使用できます。  前のセクションでは、カスタム バインディングを使用する 1 番目の方法が説明されています。  カスタム バインディングを使用すれば、バインド要素の任意のセットに基づいて独自のバインディングを作成できます。ユーザーが作成するバインディング エレメントもこれに含まれます。  
  
 2 つ以上のアプリケーションでバインディングを使用する場合、独自のバインディングを作成し、<xref:System.ServiceModel.Channels.Binding> を拡張します。  これにより、カスタム バインディングを使う必要があるたびに、手動でカスタム バインディングを作成する必要性を回避できます。  ユーザー定義のバインディングを使用して、バインディングの動作を定義したり、ユーザー定義のバインド要素を格納することができます。  また、*事前パッケージング*であるため、使用するたびにバインディングを再作成する必要はありません。  
  
 ユーザー定義のバインディングは、少なくとも <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> メソッドと <xref:System.ServiceModel.Channels.Binding.Scheme%2A> プロパティを実装する必要があります。  
  
 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> メソッドは、バインディングのバインド要素を格納している新しい <xref:System.ServiceModel.Channels.BindingElementCollection> を返します。  このコレクションは順序付けられており、始めにプロトコル バインド要素を格納し、次にエンコーディング バインド要素、その次にトランスポート バインド要素を格納する必要があります。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] システム指定のバインド要素を使用する場合、[カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)に指定されているバインド要素の順序ルールに従う必要があります。  このコレクションから、ユーザー定義のバインディング クラス内で参照されるオブジェクトを参照すべきではありません。このため、バインディングの作成者は、<xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> を呼び出すたびに <xref:System.ServiceModel.Channels.BindingElementCollection> の `Clone()` を返す必要があります。  
  
 <xref:System.ServiceModel.Channels.Binding.Scheme%2A> プロパティは、バインディングで使用するトランスポート プロトコルの URI スキームを表します。  たとえば、*WSHttpBinding* および *NetTcpBinding* は、それぞれの <xref:System.ServiceModel.Channels.Binding.Scheme%2A> プロパティから "http" および "net.tcp" を返します。  
  
 ユーザー定義バインディングのオプション メソッドとプロパティの完全な一覧については、<xref:System.ServiceModel.Channels.Binding> を参照してください。  
  
### 例  
 このサンプルでは、プロファイル バインディングを、<xref:System.ServiceModel.Channels.Binding> から派生した `SampleProfileUdpBinding` に実装します。  `SampleProfileUdpBinding` は最大で 4 つのバインド要素を格納します。1 つはユーザー作成の `UdpTransportBindingElement` で、後の 3 つはシステム指定の `TextMessageEncodingBindingElement`、 `CompositeDuplexBindingElement`、`ReliableSessionBindingElement` です。  
  
```  
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
## 双方向コントラクトのセキュリティ制限  
 すべてのバインド要素どうしに互換性があるわけではありません。  特に双方向コントラクトで使用する場合、セキュリティ バインド要素にはいくつかの制限があります。  
  
### ワンショット セキュリティ  
 \<message\> 構成要素の `negotiateServiceCredential` 属性を `false` に設定すると、必要なすべてのセキュリティ資格情報を 1 つのメッセージで送信する、"ワンショット" セキュリティを実装できます。  
  
 ワンショット認証は双方向コントラクトでは動作しません。  
  
 要求\/応答コントラクトでは、セキュリティ バインド要素の下にあるバインディング スタックで <xref:System.ServiceModel.Channels.IRequestChannel> インスタンスまたは <xref:System.ServiceModel.Channels.IRequestSessionChannel> インスタンスの作成がサポートされている場合にのみ、ワンショット認証は動作します。  
  
 一方向コントラクトでは、セキュリティ バインド要素の下にあるバインディング スタックで <xref:System.ServiceModel.Channels.IRequestChannel>、<xref:System.ServiceModel.Channels.IRequestSessionChannel>、<xref:System.ServiceModel.Channels.IOutputChannel>、または <xref:System.ServiceModel.Channels.IOutputSessionChannel> の各インスタンスの作成がサポートされている場合にのみ、ワンショット認証は動作します。  
  
### クッキー モードのセキュリティ コンテキスト トークン  
 クッキー モードのセキュリティ コンテキスト トークンは、双方向コントラクトでは使用できません。  
  
 要求\/応答コントラクトでは、セキュリティ バインド要素の下にあるバインディング スタックで <xref:System.ServiceModel.Channels.IRequestChannel> インスタンスまたは <xref:System.ServiceModel.Channels.IRequestSessionChannel> インスタンスの作成がサポートされている場合にのみ、クッキー モードのセキュリティ コンテキスト トークンは動作します。  
  
 一方向コントラクトでは、セキュリティ バインド要素の下にあるバインディング スタックで <xref:System.ServiceModel.Channels.IRequestChannel> インスタンスまたは <xref:System.ServiceModel.Channels.IRequestSessionChannel> インスタンスの作成がサポートされている場合にのみ、クッキー モードのセキュリティ コンテキスト トークンは動作します。  
  
### セッション モードのセキュリティ コンテキスト トークン  
 双方向コントラクトでは、セッション モードの SCT \(セキュリティ コンテキスト トークン\) は、セキュリティ バインド要素の下にあるバインディング スタックで <xref:System.ServiceModel.Channels.IDuplexChannel> インスタンスまたは <xref:System.ServiceModel.Channels.IDuplexSessionChannel> インスタンスの作成がサポートされている場合に動作します。  
  
 要求\/応答コントラクトでは、セッション モードの SCT は、セキュリティ バインド要素の下にあるバインディング スタックで <xref:System.ServiceModel.Channels.IDuplexChannel>、<xref:System.ServiceModel.Channels.IDuplexSessionChannel>、<xref:System.ServiceModel.Channels.IRequestChannel>、または <xref:System.ServiceModel.Channels.IRequestSessionChannel> の各インスタンスの作成がサポートされている場合に動作します。  
  
 一方向コントラクトでは、セッション モードの SCT は、セキュリティ バインド要素の下にあるバインディング スタックで <xref:System.ServiceModel.Channels.IDuplexChannel>、<xref:System.ServiceModel.Channels.IDuplexSessionChannel>、<xref:System.ServiceModel.Channels.IRequestChannel>、または <xref:System.ServiceModel.Channels.IRequestSessionChannel> の各インスタンスの作成がサポートされている場合に動作します。  
  
## 標準バインディングからの派生  
 まったく新しいバインディング クラスを作成する代わりに、システムから提供される既存のバインディングの 1 つを拡張することができます。  前述の場合と同様、<xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> メソッドと <xref:System.ServiceModel.Channels.Binding.Scheme%2A> プロパティを上書きする必要があります。  
  
## 参照  
 <xref:System.ServiceModel.Channels.Binding>   
 [カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)