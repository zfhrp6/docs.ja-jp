---
title: "クライアントを使用したサービスへのアクセス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# クライアントを使用したサービスへのアクセス
クライアント アプリケーションがサービスと通信するには、クライアント アプリケーションで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントまたはチャネルを作成および構成し、使用する必要があります。  「[WCF クライアントの概要](../../../../docs/framework/wcf/wcf-client-overview.md)」では、オブジェクトの概要および基本的なクライアントやチャネル オブジェクトの作成と使用に関する手順を説明しています。  
  
 このトピックでは、ユーザーのシナリオに応じて役立つ、クライアント アプリケーション、クライアント オブジェクト、およびチャネル オブジェクトに関するいくつかの問題について詳しく説明します。  
  
## 概要  
 ここでは、以下の項目に関連する動作と問題について説明します。  
  
-   チャネルとセッションの有効期間  
  
-   例外処理  
  
-   ブロックの問題について  
  
-   対話方式によるチャネルの初期化  
  
### チャネルとセッションの有効期間  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーションのチャネルは、データグラム チャネルとセッションフル チャネルの 2 つに分類されます。  
  
 *データグラム* チャネルは、含まれているすべてのメッセージとの相関関係のないチャネルです。  データグラム チャネルでは、入出力操作が失敗しても、通常、次の操作は影響を受けないので、同じチャネルの再利用が可能です。  したがって、通常、データグラム チャネルは失敗になりません。  
  
 一方、*セッションフル* チャネルは、他のエンドポイントと関連付けられたチャネルです。  一方のセッション内のメッセージは、他方の同じセッションと常に関連付けられています。  さらに、セッションが成功したとみなされるためには、セッションの両参加要素が、メッセージ交換要件が満たされたということに同意する必要があります。  両参加要素が同意できない場合、セッション チャネルは失敗になる場合があります。  
  
 クライアントを明示的に開く場合も暗黙的に開く場合も、最初の操作を呼び出します。  
  
> [!NOTE]
>  一般的に、障害が生じたセッションフル チャネルを明示的に検出することは有用ではありません。通知されるタイミングがセッションの実装により異なるためです。  たとえば、<xref:System.ServiceModel.NetTcpBinding?displayProperty=fullName> \(信頼できるセッションは無効\) では TCP 接続のセッションが表面に出るため、サービスまたはクライアントで <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=fullName> イベントをリッスンしていれば、ネットワーク エラーが発生すると直ちに通知される可能性があります。  一方、信頼できるセッション \(<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=fullName> を有効化したバインディングにより確立される\) は、サービスが小さなネットワーク エラーから分離されるように設計されています。  妥当な期間内にセッションの再確立が可能な場合、信頼できるセッション用に構成された、この同じバインディングは、中断が長期間発生し続けるまでエラーにならない場合があります。  
  
 アプリケーション層にチャネルを公開するほとんどのシステム提供のバインディングでは、既定でセッションが使用されますが、<xref:System.ServiceModel.BasicHttpBinding?displayProperty=fullName> では使用されません。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [セッションの使用](../../../../docs/framework/wcf/using-sessions.md).  
  
### セッションの適切な使用  
 セッションを使用すると、メッセージ交換全体が完了したかどうか、そしてメッセージ交換が成功したと両側が見なしたかどうかを認識できます。  呼び出し側のアプリケーションでは、チャネルを開き、使用して、閉じるまでを 1 つの try ブロック内で処理することをお勧めします。  セッション チャネルが開いているときに、<xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=fullName> メソッドを 1 回呼び出して、その呼び出しが正常に返された場合、セッションは成功しています。  この場合の成功とは、バインディングにより指定されているすべての配信保証が満たされ、もう一方の側では <xref:System.ServiceModel.ICommunicationObject.Close%2A> を呼び出す前にチャネルに対して <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=fullName> を呼び出さなかったことを意味します。  
  
 次のセクションで、このクライアントによる方法の例を示します。  
  
### 例外処理  
 クライアント アプリケーションで例外を処理することは簡単です。  try ブロック内部でチャネルを開き、使用して、閉じた場合、例外がスローされない限り、メッセージ交換は正常に行われています。  通常、例外がスローされた場合は、メッセージ交換が中止されます。  
  
> [!NOTE]
>  `using` ステートメント \([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] では `Using`\) を使用することはお勧めできません。  その理由は、`using` ステートメントの最後で例外が発生し、認識する必要のある他の例外がマスクされる可能性があるためです。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Using ステートメントに関する問題の回避](../../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 次のコード例は、`using` 文ではなく try\/catch ブロックを使用する、推奨されるクライアント パターンを示しています。  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
>  <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=fullName> プロパティの値を確認すると競合状態になるので、チャネルを再利用するかどうか、またはチャネルを閉じるかどうかを決定するのにこの値を確認することは推奨されません。  
  
 データグラム チャネルを閉じるときに例外が発生しても、データグラム チャネルはエラーになりません。  さらに、非双方向クライアントがセキュリティで保護されたメッセージ交換を使用して認証に失敗した場合、通常、<xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=fullName> がスローされます。  しかし、双方向クライアントがセキュリティで保護されたメッセージ交換を使用して認証に失敗した場合、クライアントは代わりに <xref:System.TimeoutException?displayProperty=fullName> を受信します。  
  
 アプリケーション レベルでのエラー情報の処理の詳細については、「[コントラクトおよびサービスのエラーの指定と処理](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)」を参照してください。  予期される例外とその処理方法については、「[予期される例外](../../../../docs/framework/wcf/samples/expected-exceptions.md)」を参照してください。  チャネル開発時のエラーの処理方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[例外とエラーの処理](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)」を参照してください。  
  
### クライアントのブロックとパフォーマンス  
 アプリケーションが要求\/応答操作を同期的に呼び出す場合、戻り値が受信されるか例外 \(<xref:System.TimeoutException?displayProperty=fullName> など\) がスローされるまで、クライアントはブロックされます。  この動作はローカルの動作と似ています。  アプリケーションが [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント オブジェクトまたはチャネルに対する操作を同期的に呼び出す場合、チャネル レイヤーがデータをネットワークに書き込むことができるまで、または例外がスローされるまで、クライアントに制御は戻りません。  また、一方向メッセージ交換パターン \(<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=fullName> が `true` に設定された操作をマークすることで指定される\) では、クライアントの応答性が向上する可能性がありますが、バインディングや送信済みのメッセージによっては、一方向操作でもブロックが生じる場合があります。  一方向操作とはメッセージ交換のみを指しています。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [一方向サービス](../../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
 メッセージ交換パターンに関係なく、大規模データのチャンクによりクライアント処理が遅延する場合があります。  この問題の処理方法を理解するには、「[大規模データとストリーミング](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)」を参照してください。  
  
 操作が完了してもアプリケーションでさらに処理を行う必要がある場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントが実装するサービス コントラクト インターフェイスに非同期のメソッドのペアを作成する必要があります。  これを行うには、[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) で `/async` スイッチを使用するのが最も簡単な方法です。  例については、「[方法 : サービス操作を非同期に呼び出す](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)」を参照してください。  
  
 クライアントのパフォーマンス向上[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[中間層クライアント アプリケーション](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)」を参照してください。  
  
### ユーザーによる資格情報の動的選択の有効化  
 <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> インターフェイスを使用すると、アプリケーションによりユーザー インターフェイスが表示され、ユーザーが資格情報を選択できるようになります。この資格情報は、タイムアウト タイマーが開始される前に、チャネルの作成に使用されます。  
  
 アプリケーション開発者は、挿入された <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> を 2 つの方法で利用できます。  チャネルを開く前 \(*明示的*方法\)、または最初の操作を呼び出す前 \(*暗黙的*方法\) に、クライアント アプリケーションで <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=fullName> または <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=fullName> \(または非同期バージョン\) を呼び出すことができます。  
  
 暗黙的方法を使用する場合、アプリケーションは最初の操作を <xref:System.ServiceModel.ClientBase%601> または <xref:System.ServiceModel.IClientChannel> 拡張に対して呼び出す必要があります。  アプリケーションが最初の操作以外の何かを呼び出した場合、例外がスローされます。  
  
 明示的方法を使用する場合、アプリケーションで次の手順を順番に実行する必要があります。  
  
1.  <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=fullName> または <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=fullName> \(または非同期バージョン\) を呼び出します。  
  
2.  初期化子が返された場合は、<xref:System.ServiceModel.IClientChannel> オブジェクトまたは <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=fullName> プロパティで返された <xref:System.ServiceModel.IClientChannel> オブジェクトの <xref:System.ServiceModel.ICommunicationObject.Open%2A> メソッドを呼び出します。  
  
3.  操作を呼び出します。  
  
 製品品質のアプリケーションでは、明示的な方法を採用することによってユーザー インターフェイスのプロセスを制御することをお勧めします。  
  
 暗黙的な方法を使用するアプリケーションでは、ユーザー インターフェイス初期化子が呼び出されますが、このアプリケーションのユーザーがバインディングの送信タイムアウト期間内に応答できない場合、ユーザー インターフェイスが復帰すると例外がスローされます。  
  
## 参照  
 [双方向サービス](../../../../docs/framework/wcf/feature-details/duplex-services.md)   
 [方法 : 一方向コントラクトと要求\/応答コントラクトを使用してサービスにアクセスする](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)   
 [方法 : 双方向コントラクトを使用してサービスにアクセスする](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)   
 [方法 : WSE 3.0 サービスにアクセスする](../../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)   
 [方法 : ChannelFactory を使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)   
 [方法 : サービス操作を非同期に呼び出す](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)   
 [中間層クライアント アプリケーション](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)