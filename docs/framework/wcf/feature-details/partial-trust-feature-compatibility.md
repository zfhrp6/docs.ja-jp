---
title: 部分信頼機能の互換性
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
caps.latest.revision: 75
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 72282c62ad23ec825eab7054ab1909d07a062b45
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="partial-trust-feature-compatibility"></a>部分信頼機能の互換性
部分信頼環境で実行される場合、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] でサポートされる機能は、限られたサブセットになります。 部分信頼でサポートされる機能は、「 [Supported Deployment Scenarios](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md) 」のトピックで説明される特定のシナリオを念頭にデザインされています。  
  
## <a name="minimum-permission-requirements"></a>最小のアクセス許可の要件  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、次の標準の名前付きアクセス許可セットのいずれかで実行されるアプリケーションの機能のサブセットをサポートします。  
  
-   中程度の信頼アクセス許可  
  
-   インターネット ゾーン アクセス許可  
  
 これよりも制限の厳しいアクセス許可が設定された部分信頼アプリケーションで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用すると、実行時にセキュリティ例外が発生することがあります。  
  
## <a name="contracts"></a>コントラクト  
 部分信頼で実行される場合、コントラクトには次の制限があります。  
  
-   `[ServiceContract]` インターフェイスを実装するサービス クラスは、 `public` であること、および `public` コンストラクターを持っていることが必要です。 このクラスで `[OperationContract]` メソッドを定義する場合、それらも `public`である必要があります。 代わりに `[ServiceContract]` インターフェイスを実装する場合は、 `private`インターフェイスが `[ServiceContract]` であれば、それらのメソッド実装は明示的でも `public`でもかまいません。  
  
-   `[ServiceKnownType]` 属性を使用するときは、指定するメソッドは `public`である必要があります。  
  
-   `[MessageContract]` クラスとそのメンバーは、 `public`である場合があります。 `[MessageContract]` クラスがアプリケーション アセンブリで定義されている場合は、 `internal` であり、 `internal` メンバーを持つ場合があります。  
  
## <a name="system-provided-bindings"></a>システム標準のバインディング  
 部分信頼環境では、 <xref:System.ServiceModel.BasicHttpBinding> と <xref:System.ServiceModel.WebHttpBinding> が完全にサポートされています。 <xref:System.ServiceModel.WSHttpBinding> は、トランスポート セキュリティ モードでのみサポートされます。  
  
 <xref:System.ServiceModel.NetTcpBinding>、 <xref:System.ServiceModel.NetNamedPipeBinding>、または <xref:System.ServiceModel.NetMsmqBinding>など、HTTP 以外のトランスポートを使用するバインディングは、部分信頼環境で実行される場合はサポートされません。  
  
## <a name="custom-bindings"></a>カスタム バインディング  
 部分信頼環境ではカスタム バインディングの作成と使用が可能ですが、このセクションに示した制限に従う必要があります。  
  
### <a name="transports"></a>トランスポート  
 使用できるトランスポート バインド要素は、 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> と <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>に限られます。  
  
### <a name="encoders"></a>エンコーダー  
 次のエンコーダーを指定できます。  
  
-   テキスト エンコーダー (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>)  
  
-   バイナリ エンコーダー (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>)  
  
-   Web メッセージ エンコーダー (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>)  
  
 MTOM (Message Transmission Optimization Mechanism) エンコーダーはサポートされていません。  
  
### <a name="security"></a>セキュリティ  
 部分信頼アプリケーションは、通信をセキュリティで保護するために [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]のトランスポート レベルのセキュリティ機能を使用することがあります。 メッセージ レベルのセキュリティはサポートされていません。 メッセージ レベルのセキュリティを使用するようにバインディングを構成すると、実行時に例外が発生します。  
  
### <a name="unsupported-bindings"></a>サポートされないバインディング  
 信頼できるメッセージング、トランザクション、またはメッセージ レベルのセキュリティを使用するバインディングはサポートされません。  
  
## <a name="serialization"></a>シリアル化  
 部分信頼環境では、 <xref:System.Runtime.Serialization.DataContractSerializer> と <xref:System.Xml.Serialization.XmlSerializer> の両方がサポートされています。 ただし、 <xref:System.Runtime.Serialization.DataContractSerializer> の使用は、次の条件に従う必要があります。  
  
-   シリアル化可能なすべての `[DataContract]` 型は `public`である必要があります。  
  
-   `[DataMember]` 型にあるシリアル化可能なすべての `[DataContract]` フィールドまたはプロパティは、パブリックで読み書き可能である必要があります。 [読み取り専用](http://go.microsoft.com/fwlink/?LinkID=98854) フィールドのシリアル化と逆シリアル化は、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を部分信頼アプリケーションで実行する場合にはサポートされません。  
  
-   部分信頼環境では、 `[Serializable]`/ISerializable プログラミング モデルはサポートされていません。  
  
-   既知の型はコード内、またはマシン レベルの構成 (machine.config) で指定する必要があります。 既知の型はセキュリティ上の理由からアプリケーション レベルの構成では指定できません。  
  
-   <xref:System.Runtime.Serialization.IObjectReference> を実装する型は、部分信頼環境では例外をスローします。  
  
 部分信頼アプリケーションで [T:System.Runtime.Serialization.DataContractSerializer](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) を安全に使用する場合のセキュリティ情報の詳細については、「 <xref:System.Runtime.Serialization.DataContractSerializer> 」のシリアル化のセクションを参照してください。  
  
### <a name="collection-types"></a>コレクション型  
 コレクション型の中には、 <xref:System.Collections.Generic.IEnumerable%601> と <xref:System.Collections.IEnumerable>の両方を実装するものがあります。 たとえば、 <xref:System.Collections.Generic.ICollection%601>を実装する型がこれに当たります。 このような型では、 `public` の `GetEnumerator()`な実装と、 `GetEnumerator()`の明示的な実装を実装できます。 この場合、 <xref:System.Runtime.Serialization.DataContractSerializer> は `public` の `GetEnumerator()`な実装を呼び出し、 `GetEnumerator()`の明示的な実装は呼び出しません。 `GetEnumerator()` 実装のいずれも `public` ではなく、すべてが明示的な実装である場合、 <xref:System.Runtime.Serialization.DataContractSerializer> は `IEnumerable.GetEnumerator()`を呼び出します。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が部分信頼環境で実行されているときに、コレクション型の `GetEnumerator()` の実装がどれも `public`ではなく、またそのどれもが明示的なインターフェイスの実装でない場合は、セキュリティ例外がスローされます。  
  
### <a name="netdatacontractserializer"></a>NetDataContractSerializer  
 部分信頼の場合、 <xref:System.Collections.Generic.List%601>、 <xref:System.Collections.ArrayList>、 <xref:System.Collections.Generic.Dictionary%602> 、および <xref:System.Collections.Hashtable> などの、.NET Framework コレクション型の多くは、 <xref:System.Runtime.Serialization.NetDataContractSerializer> によってサポートされていません。 これらの型には `[Serializable]` 属性セットがあり、シリアル化のセクションで説明したように、この属性は部分信頼ではサポートされません。 <xref:System.Runtime.Serialization.DataContractSerializer> はコレクションを特殊な方法で扱うため、この制限を回避できますが、 <xref:System.Runtime.Serialization.NetDataContractSerializer> には、この制限の適用を避けるメカニズムはありません。  
  
 <xref:System.DateTimeOffset> 型は、部分信頼では <xref:System.Runtime.Serialization.NetDataContractSerializer> によってサポートされません。  
  
 部分信頼で実行するときは、( <xref:System.Runtime.Serialization.NetDataContractSerializer> メカニズムを使用して) <xref:System.Runtime.Serialization.SurrogateSelector> でサロゲートを使用できません。 この制限は、シリアル化ではなく、サロゲートの使用に適用されることに注意してください。  
  
## <a name="enabling-common-behaviors-to-run"></a>実行する共通動作の有効化  
 サービスまたはエンドポイントの動作でマークされていない、<xref:System.Security.AllowPartiallyTrustedCallersAttribute>属性 (APTCA) に追加される、 [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)部分的な信頼でアプリケーションを実行すると、構成ファイルのセクションが実行されませんこのエラーが発生、環境と例外がスローされません。 共通動作を強制的に実行するには、次のいずれかを行う必要があります。  
  
-   共通動作を <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性でマークし、部分信頼アプリケーションとして展開したときに実行できるようにします。 APTCA でマークされたアセンブリを実行できないように、コンピューターでレジストリ エントリを設定できます。 である必要があります。  
  
-   アプリケーションが完全信頼アプリケーションとして配置されている場合に、ユーザーが部分信頼環境でアプリケーションを実行するようにコード アクセス セキュリティ設定を変更できないことを確認します。 ユーザーがこのような変更を行うことができる場合、動作は実行されず、例外もスローされません。 これには、次を参照してください。、 **levelfinal**オプションを使用して[Caspol.exe (コード アクセス セキュリティ ポリシー ツール)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)です。  
  
 共通の動作の例は、次を参照してください。[する方法: 企業内のロックのダウン エンドポイント](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)です。  
  
## <a name="configuration"></a>構成  
 1 つの例外を除き、部分信頼コードは、ローカルの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ファイルにある `app.config` 構成セクションのみを読み込むことができます。 machine.config ファイルまたはルート web.config ファイルの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セクションを参照する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 構成セクションを読み込むには、ConfigurationPermission(Unrestricted) が必要です。 このアクセス許可がない場合、ローカルの構成ファイル外の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 構成セクション (behaviors、bindings) を参照すると、構成の読み込み時に例外が発生します。  
  
 例外は、このトピックのシリアル化のセクションで説明したように、シリアル化の既知の型の構成です。  
  
> [!IMPORTANT]
>  構成の拡張は、完全信頼で実行される場合にのみサポートされます。  
  
## <a name="diagnostics"></a>診断  
  
### <a name="event-logging"></a>イベント ログ  
 部分信頼では、限定されたイベント ログがサポートされます。 イベント ログには、サービス アクティベーション エラーおよびトレース/メッセージ ログ エラーのみが記録されます。 イベント ログに過剰な数のメッセージが書き込まれないように、ログに記録できるイベントの最大数は 5 つです。  
  
### <a name="message-logging"></a>メッセージ ログ  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が部分信頼環境で実行されていると、メッセージ ログは動作しません。 部分信頼環境下で有効になっても、サービスのアクティブ化には失敗しませんが、メッセージはログに記録されません。  
  
### <a name="tracing"></a>トレース  
 部分信頼環境で実行される場合、利用できるトレース機能には制限があります。 構成ファイルの <`listeners`> 要素に追加できる型は <xref:System.Diagnostics.TextWriterTraceListener> と新しい <xref:System.Diagnostics.EventSchemaTraceListener> に限られます。 標準の <xref:System.Diagnostics.XmlWriterTraceListener> を使用すると、ログが不完全または不正確になります。  
  
 次のトレース ソースがサポートされています。  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.Runtime.Serialization>  
  
-   <xref:System.IdentityModel.Claims>、 <xref:System.IdentityModel.Policy>、 <xref:System.IdentityModel.Selectors>、および <xref:System.IdentityModel.Tokens>。  
  
 次のトレース ソースはサポートされていません。  
  
-   CardSpace  
  
-   <xref:System.IO.Log>  

-   [System.ServiceModel.Internal.TransactionBridge](https://msdn.microsoft.com/library/system.servicemodel.internal.transactionbridge.aspx)]
  
 <xref:System.Diagnostics.TraceOptions> 列挙体の次のメンバーは指定できません。  
  
-   <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 部分信頼環境でトレースを使用する場合は、アプリケーションにトレース リスナーの出力を保存するための十分なアクセス許可があることを確認します。 たとえば、 <xref:System.Diagnostics.TextWriterTraceListener> を使用してトレース出力をテキスト ファイルに書き込む場合は、アプリケーションにトレース ファイルを書き込むために必要な FileIOPermission があることを確認します。  
  
> [!NOTE]
>  トレース ファイルが重複したエラーでいっぱいになるのを防ぐために、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では最初のセキュリティ エラーの後でリソースまたはアクションのトレースを無効にします。 リソースへのアクセスまたはアクションの実行が初めて行われようとしたとき、例外トレースはリソース アクセスの各失敗に対して、1 回だけ行われます。  
  
## <a name="wcf-service-host"></a>WCF サービス ホスト  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス ホストは、部分信頼をサポートしません。 部分信頼において [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを使用する場合は、サービスをビルドするために [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] にある [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] サービス ライブラリ プロジェクト テンプレートを使用しないでください。 代わりに、 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 部分信頼がサポートされている Web サーバーでサービスをホストできる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス Web サイト テンプレートを選択して、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に新しい Web サイトを作成します。  
  
## <a name="other-limitations"></a>他の制約  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は通常、ホスト アプリケーションによってもたらされるセキュリティ上の考慮事項によって制限されます。 たとえば、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が XAML ブラウザー アプリケーション (XBAP) でホストされている場合は、「 [Windows Presentation Foundation 部分信頼セキュリティ](http://go.microsoft.com/fwlink/?LinkId=89138)」で説明されているように、XBAP の制限に従うことになります。  
  
 次の追加機能は indigo2 が部分信頼環境で実行されていると有効になりません。  
  
-   WMI (Windows Management Instrumentation)  
  
-   イベント ログは部分的にしか有効になりません (**診断の**セクションの説明を参照 )。  
  
-   パフォーマンス カウンター  
  
 部分信頼環境でサポートされていない [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 機能を使用すると、実行時に例外が発生することがあります。  
  
## <a name="unlisted-features"></a>記載されていない機能  
 部分信頼環境で利用できない情報やアクションを見つけ出す最善の方法は、リソースへのアクセスまたはアクションの実行を `try` ブロックの内側で試みて、エラーを `catch` することです。 トレース ファイルが重複したエラーでいっぱいになるのを防ぐために、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では最初のセキュリティ エラーの後でリソースまたはアクションのトレースを無効にします。 リソースへのアクセスまたはアクションの実行が初めて行われようとしたとき、例外トレースはリソース アクセスの各失敗に対して、1 回だけ行われます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [サポートされている配置シナリオ](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)  
 [部分信頼のベスト プラクティス](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)
