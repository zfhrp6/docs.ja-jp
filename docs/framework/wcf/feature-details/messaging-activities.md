---
title: "メッセージング アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 67a14c70f6287f1d37e6c855589d86aeba395c24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="messaging-activities"></a>メッセージング アクティビティ
アクティビティを管理することで、ワークフローが WCF メッセージを送受信できるようになります。 メッセージング アクティビティをワークフローに追加することで、任意に複雑なメッセージ交換パターン (MEP) をモデル化できます。  
  
## <a name="message-exchange-patterns"></a>メッセージ交換パターン  
 基本的なメッセージ交換パターンは、次の 3 種類です。  
  
-   **データグラム**- データグラム MEP を使用する場合、クライアント メッセージを送信、サービスが、サービスは応答しません。 これは、"ファイア アンド フォーゲット (撃ち放し)" と呼ばれる場合があります。 このような交換では、配信の成否について帯域外での確認が必要になります。 メッセージが移動中に失われて、サービスに到達しない可能性があります。 クライアントが正常にメッセージを送信した場合でも、サービスがメッセージを受信したとは限りません。 サービスは、メッセージングの不可欠な構成要素であり、これを基盤として独自の MEP を構築できます。  
  
-   **要求-応答**- クライアントの要求-応答 MEP を使用して送信すると、サービスにメッセージが必要な処理と、クライアントにバックアップを作成し、応答が送信されます。 パターンは、要求 - 応答のペアで構成されます。 要求 - 応答呼び出しの例として、リモート プロシージャ コール (RPC) やブラウザー GET 要求などがあります。 このパターンは、半二重とも呼ばれます。  
  
-   **双方向**- する場合は、双方向 MEP クライアントとサービスを使用してメッセージを送信できます互いに任意の順序で。 二重 MEP は、話される語の 1 つずつがメッセージである電話の会話に似ています。  
  
 メッセージング アクティビティを使用すると、これらの基本の MEP のほかに、任意の複雑な MEP を実装できます。  
  
## <a name="messaging-activities"></a>メッセージング アクティビティ  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] では、次のメッセージング アクティビティが定義されています。  
  
-   <xref:System.ServiceModel.Activities.Send> - メッセージの送信には <xref:System.ServiceModel.Activities.Send> アクティビティを使用します。  
  
-   <xref:System.ServiceModel.Activities.SendReply> - 受信したメッセージに対する応答の送信には、<xref:System.ServiceModel.Activities.SendReply> アクティビティを使用します。 このアクティビティは、要求/応答 MEP を実装した場合に、ワークフロー サービスによって使用されます。  
  
-   <xref:System.ServiceModel.Activities.Receive>- メッセージの受信には <xref:System.ServiceModel.Activities.Receive> アクティビティを使用します。  
  
-   <xref:System.ServiceModel.Activities.ReceiveReply> - 応答メッセージの受信には <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティを使用します。 このアクティビティは、要求/応答 MEP を実装した場合に、ワークフロー サービス クライアントによって使用されます。  
  
## <a name="messaging-activities-and-message-exchange-patterns"></a>メッセージング アクティビティとメッセージ交換パターン  
 データグラム MEP には、メッセージを送信するクライアントとメッセージを受信するサービスが必要です。 クライアントがワークフローの場合は、<xref:System.ServiceModel.Activities.Send> アクティビティを使用してメッセージを送信します。 そのメッセージをワークフローで受信するには、<xref:System.ServiceModel.Activities.Receive> アクティビティを使用します。 <xref:System.ServiceModel.Activities.Send> アクティビティと <xref:System.ServiceModel.Activities.Receive> アクティビティのどちらにも、`Content` という名前のプロパティがあります。 このプロパティには、送信または受信されるデータが保持されます。 要求 - 応答 MEP を実装する場合は、クライアントとサービスの両方で、アクティビティの組を使用します。 クライアントは、<xref:System.ServiceModel.Activities.Send> アクティビティを使用してメッセージを送信し、<xref:System.ServiceModel.Activities.ReceiveReply> アクティビティを使用してサービスからの応答を受信します。 これらの 2 つのアクティビティは、<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> プロパティによって互いに関連付けられています。 このプロパティは、元のメッセージを送信した <xref:System.ServiceModel.Activities.Send> アクティビティに設定されます。 サービスも、相互に関連付けられた、<xref:System.ServiceModel.Activities.Receive> および <xref:System.ServiceModel.Activities.SendReply> というアクティビティのペアを使用します。 これらの 2 つのアクティビティは、<xref:System.ServiceModel.Activities.SendReply.Request%2A> プロパティによって関連付けられています。 このプロパティは、元のメッセージを受信した <xref:System.ServiceModel.Activities.Receive> アクティビティに設定されます。 <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティおよび <xref:System.ServiceModel.Activities.SendReply> アクティビティを使用すると、<xref:System.ServiceModel.Activities.Send> アクティビティおよび <xref:System.ServiceModel.Activities.Receive> アクティビティと同様に、<xref:System.ServiceModel.Channels.Message> インスタンスまたはメッセージ コントラクト型を送信できます。  
  
 ワークフローは長時間にわたって実行されることが多いため、通信の二重パターンでは、長時間のメッセージ交換をサポートすることも重要です。 長時間のメッセージ交換をサポートするには、メッセージ交換を開始するクライアントが、後でデータが利用可能になった時点でクライアントにコールバックする機会をサービスに提供する必要があります。 たとえば、マネージャーの承認を受けるために発注書の要求が送信された場合に、この要求が、1 日、1 週間、または 1 年間処理されない可能性があるとします。この場合、マネージャーが発注書を承認するワークフローは、承認を受けた後に再開することを認識している必要があります。 この二重通信のパターンは、相関関係を使用するワークフローでサポートされています。 二重パターンを実装するには、<xref:System.ServiceModel.Activities.Send> アクティビティと <xref:System.ServiceModel.Activities.Receive> アクティビティを使用します。 <xref:System.ServiceModel.Activities.Receive>アクティビティ、相関関係の特殊なキーの値を使用して、初期化<!--zz <xref:System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName%2A>-->`System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName`です。 <xref:System.ServiceModel.Activities.Send> アクティビティで、その関連付けハンドルを <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> プロパティの値として設定します。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][永続的な二重](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md)です。  
  
> [!NOTE]
>  双方向コールバック相関関係 ("永続的な二重") の使用のワークフローの実装は、長時間のメッセージ交換です。 これは、コールバック コントラクトを使用する WCF の二重と同じではありません。WCF の二重では、メッセージ交換が短時間 (チャネルの有効期間) で処理されます。  
  
## <a name="message-formatting-and-messaging-activities"></a>メッセージの書式設定とメッセージング アクティビティ  
 <xref:System.ServiceModel.Activities.Receive> アクティビティと <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティには、`Content` という名前のプロパティがあります。 このプロパティは <xref:System.ServiceModel.Activities.ReceiveContent> 型で、<xref:System.ServiceModel.Activities.Receive> アクティビティまたは <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティが受信するデータを表します。 .NET Framework では、<xref:System.ServiceModel.Activities.ReceiveMessageContent> および <xref:System.ServiceModel.Activities.ReceiveParametersContent> という 2 つの関連クラスが定義されています。どちらも、<xref:System.ServiceModel.Activities.ReceiveContent> から派生しています。 ワークフロー サービスでデータを受信するには、<xref:System.ServiceModel.Activities.Receive> アクティビティまたは <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティの `Content` プロパティを、これらの型のいずれかのインスタンスに設定します。 どの型を使用するかは、アクティビティが受信するデータの型によって異なります。 アクティビティが `Message` オブジェクト型またはメッセージ コントラクト型を受信する場合は、<xref:System.ServiceModel.Activities.ReceiveMessageContent> を使用します。 シリアル化できるデータ コントラクトまたは XML 型をアクティビティが受信した場合には、<xref:System.ServiceModel.Activities.ReceiveParametersContent> を使用します。 <xref:System.ServiceModel.Activities.ReceiveParametersContent> では複数のパラメーターを送信できますが、<xref:System.ServiceModel.Activities.ReceiveMessageContent> で送信できるのは、1 つのオブジェクト、つまり、メッセージ (またはメッセージ コントラクト型) のみです。  
  
> [!NOTE]
>  <xref:System.ServiceModel.Activities.ReceiveMessageContent> は、シリアル化できるデータ コントラクトまたは XML 型が 1 つだけの場合も使用できます。 パラメーターが 1 つだけの <xref:System.ServiceModel.Activities.ReceiveParametersContent> を使用する場合と、<xref:System.ServiceModel.Activities.ReceiveMessageContent> に直接渡されるオブジェクトとの違いは、ワイヤ形式です。 パラメーターのコンテンツは、操作名に対応する XML 要素でラップされ、シリアル化されたオブジェクトは、パラメーター名を使用した XML 要素でラップされます (例: `<Echo><msg>Hello, World</msg></Echo>`)。 メッセージの内容は、操作名によってラップされません。 代わりに、シリアル化されたオブジェクトが、XML 修飾型の名前を使用して XML 要素内に格納されます (例: `<string>Hello, World</string>`)。  
  
 <xref:System.ServiceModel.Activities.Send> アクティビティと <xref:System.ServiceModel.Activities.SendReply> アクティビティにも、`Content` という名前のプロパティがあります。 このプロパティは <xref:System.ServiceModel.Activities.SendContent> 型で、<xref:System.ServiceModel.Activities.Send> アクティビティまたは <xref:System.ServiceModel.Activities.SendReply> アクティビティが送信するデータを表します。 .NET Framework では、<xref:System.ServiceModel.Activities.SendMessageContent> および <xref:System.ServiceModel.Activities.SendParametersContent> という 2 つの関連型が定義されています。どちらも、<xref:System.ServiceModel.Activities.SendContent> から派生しています。 ワークフロー サービスからデータを送信するには、<xref:System.ServiceModel.Activities.Send> アクティビティまたは <xref:System.ServiceModel.Activities.SendReply> アクティビティの `Content` プロパティを、これらの型のいずれかのインスタンスに設定します。 どの型を使用するかは、アクティビティが送信するデータの型によって異なります。 アクティビティが `Message` オブジェクト型またはメッセージ コントラクト型を送信する場合は、<xref:System.ServiceModel.Activities.SendMessageContent> を使用します。 アクティビティがデータ コントラクト型を送信する場合は、<xref:System.ServiceModel.Activities.SendParametersContent> を使用します。 <xref:System.ServiceModel.Activities.SendParametersContent> では複数のパラメーターを送信できますが、<xref:System.ServiceModel.Activities.SendMessageContent> で送信できるのは、1 つのオブジェクト、つまり、メッセージ (またはメッセージ コントラクト型) のみです。  
  
 強制的にメッセージング アクティビティを使用してプログラミングを行う場合は、汎用の <xref:System.Activities.InArgument%601> および <xref:System.Activities.OutArgument%601> を使用して、メッセージまたは <xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply>、<xref:System.ServiceModel.Activities.Receive>、および <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティのパラメーター プロパティに割り当てるオブジェクトをラップします。 使用して<xref:System.Activities.InArgument%601>の<xref:System.ServiceModel.Activities.Send>と<xref:System.ServiceModel.Activities.SendReply>アクティビティと<xref:System.Activities.OutArgument%601>の<xref:System.ServiceModel.Activities.Receive>と<xref:System.ServiceModel.Activities.ReceiveReply>アクティビティ。 `In` 引数は、データがアクティビティに渡されるため、送信アクティビティで使用されます。 `Out` 引数は、データがアクティビティから渡されるため、受信アクティビティで使用されます。この例を次に示します。  
  
```  
Receive reserveSeat = new Receive  
{   
    ...   
    Content = new ReceiveParametersContent  
    {  
        Parameters =  
        {  
            { "ReservationInfo", new OutArgument<ReservationRequest>(reservationInfo) }  
        }  
    }  
};  
SendReply reserveSeat = new SendReply  
{   
    ...   
    Request = reserveSeat,  
    Content = new SendParametersContent  
    {  
        Parameters =  
        {  
            { "ReservationId", new InArgument<string>(reservationId) }  
        }  
    },  
};  
```  
  
 void を返す要求/応答操作を定義するワークフロー サービスを実装する場合は、<xref:System.ServiceModel.Activities.SendReply> アクティビティをインスタンス化して、<xref:System.ServiceModel.Activities.SendReply.Content%2A> プロパティをコンテンツの種類 (<xref:System.ServiceModel.Activities.SendMessageContent> または <xref:System.ServiceModel.Activities.SendParametersContent>) のいずれかのインスタンスに設定します。この例を次に示します。  
  
```  
Receive rcv = new Receive()  
{  
ServiceContractName = "IService",  
OperationName = "NullReturningContract",  
Content = new ReceiveParametersContent( new Dictionary<string, OutArgument>() { { "message", new OutArgument<string>() } } )  
};  
SendReply sr = new SendReply()  
{  
Request = rcv  
   Content = new SendParametersContent();  
};  
```  
  
## <a name="add-service-reference"></a>サービス参照の追加  
 ワークフロー アプリケーションからワークフロー サービスを呼び出すと、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] では、要求/応答 MEP で使用される通常の <xref:System.ServiceModel.Activities.Send> アクティビティと <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティをカプセル化したカスタムのメッセージング アクティビティが生成されます。 この機能を使用するでクライアント プロジェクトを右クリックして[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]選択**サービス参照の追加**です。 アドレス ボックスにサービスのベース アドレスを入力し、[移動] をクリックします。 使用可能なサービスが表示されます、 **Services:**ボックス。 サービス ノードを展開して、サポートされるコントラクトを表示します。 呼び出そうとコントラクトを選択し、使用可能な操作の一覧に表示されます、 **Operations**ボックス。 生成されたアクティビティの名前空間を指定し、をクリックして**OK**です。 操作が正常に完了したことを示すダイアログが表示され、プロジェクトを再度ビルドすると、生成されたカスタム アクティビティがツールボックスに表示されます。 サービス コントラクトに定義されている操作ごとに 1 つのアクティビティがあります。 プロジェクトを再度ビルドしたら、カスタム アクティビティをワークフローにドラッグ アンド ドロップして、必要なプロパティをプロパティ ウィンドウで設定できます。  
  
<!--## Messaging Activity Templates  
 To make setting up a request/response MEP on the client and service easier, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] provides two messaging activity templates. <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> is used on the service and <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> is used on the client. In both cases the templates add the appropriate messaging activities to your workflow. On the service, the <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> adds a <xref:System.ServiceModel.Activities.Receive> activity followed by a <xref:System.ServiceModel.Activities.SendReply> activity. The <xref:System.ServiceModel.Activities.SendReply.Request> property is automatically set to the <xref:System.ServiceModel.Activities.Receive> activity. On the client, the <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> adds a <xref:System.ServiceModel.Activities.Send> activity followed by a <xref:System.ServiceModel.Activities.ReceiveReply>. The <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> property is automatically set to the <xref:System.ServiceModel.Activities.Send> activity. To use these templates, just drag and drop the appropriate template onto your workflow.  
-->
## <a name="messaging-activities-and-transactions"></a>メッセージング アクティビティとトランザクション  
 ワークフロー サービスが呼び出されるときに、サービス操作にトランザクションをフローする必要がある場合があります。 それには、<xref:System.ServiceModel.Activities.Receive> アクティビティを <xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティ内に配置します。 <xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティには、`Receive` アクティビティと本体が含まれます。 サービスにフローされるトランザクションは、<xref:System.ServiceModel.Activities.TransactedReceiveScope> の本体の実行の開始から終了まで、アンビエント トランザクションのままです。 トランザクションは、本体の実行が終了した時点で完了します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]ワークフローとトランザクションを参照してください[ワークフロー トランザクション](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ワークフロー サービスでエラーを送受信する方法](http://go.microsoft.com/fwlink/?LinkId=189151)  
 [実行時間の長いワークフロー サービスを作成します。](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
