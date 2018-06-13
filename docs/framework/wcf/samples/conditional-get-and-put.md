---
title: 条件付きの Get と Put
ms.date: 03/30/2017
ms.assetid: 3d22067f-57b8-4e0f-a571-a694512187ae
ms.openlocfilehash: f2d170da80de1186aa41b4821da52d58a0bb0e0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505731"
---
# <a name="conditional-get-and-put"></a>条件付きの Get と Put
このサンプルでは、新しい条件付きの取得 API と更新 API を WCF REST プログラミング モデルで使用する方法を示します。 条件付きの取得と更新プログラムに最も適したためリソース指向の REST サービスでは、このサンプルを拡張し、[基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)サンプルです。 このサンプルでは、条件付きの取得と更新のサポートの追加、[基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)で導入された新しい Api を使用してサンプル[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]です。  
  
## <a name="demonstrates"></a>使用例  
 条件付きの取得と更新  
  
## <a name="discussion"></a>説明  
 このサンプルの WCF サービスでは、リソース指向の REST 方式で顧客のコレクションが公開されます。 サービス実装の詳細についてを参照してください、[基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)サンプルです。  
  
 このサンプルは、条件付きの取得と更新機能を追加、[基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)サンプルです。 条件付きの取得と更新では、HTTP のエンティティ タグと HTTP の If-None-Match ヘッダーおよび If-Match ヘッダーを使用して、指定されたリソースの最新のエンティティがクライアントにあるかどうかを検証します。 しかし、HTTP の If-None-Match ヘッダーと If-Match ヘッダーを正しく解析するコードを実装することは、面倒であるだけでなく間違いの元にもなります。 そのため、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> に <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> メソッドと <xref:System.ServiceModel.Web.IncomingWebRequestContext> メソッドが追加され、<xref:System.ServiceModel.Web.WebOperationContext> の現在のインスタンスを使用してアクセスできるようになっています。 さらに、`SetETag` に <xref:System.ServiceModel.Web.OutgoingWebRequestContext> メソッドが追加されているため、有効なエンティティ タグを返すのも簡単になります。  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> メソッドは、[WebGet] 操作で使用されることを想定しています。 このメソッドは、指定されたリソースの現在のエンティティ タグを `entityTag` パラメーターとして取得します。これは、`string`、`int`、`long`、または `Guid` のいずれかになります。 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> メソッドは、エンティティ タグを要求の HTTP If-None-Match ヘッダーと照合してチェックします。 エンティティ タグが HTTP If-None-Match ヘッダーにある場合、ステータス コード 304 (変更なし) が設定された <xref:System.ServiceModel.Web.WebFaultException> がスローされます。それ以外の場合は、メソッドから制御が戻ります。 条件付きの取得メカニズムでは、クライアントからサーバーにそのエンティティを持っていることを通知し、クライアントがまだ現在のエンティティを持っていない場合にのみエンティティを送信することができます。 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> メソッドの使用例は、サービスの `GetCustomer` 操作および `GetCustomers` 操作で確認できます。 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> の呼び出しは戻らない場合があることに注意してください。 そのため、操作を実装するときは、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> の呼び出しの実行前に、要求が成功することがわかるようにする必要があります。そうすることで、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> の呼び出しがなかった場合でも、成功を示すステータス コードが設定された応答がサービスから送信されます。  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> メソッドは、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> メソッドに似ています。 このメソッドも、指定されたリソースの現在のエンティティ タグを取得します。 ただし、メソッドは、メソッドが"PUT"または"DELETE"に設定されている [WebInvoke] 操作で使用するものでは。 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> メソッドは、エンティティ タグを要求の HTTP If-Match ヘッダーと照合してチェックします。 エンティティ タグが HTTP If-Match ヘッダーにない場合、ステータス コード 412 (必須条件に失敗しました) が設定された <xref:System.ServiceModel.Web.WebFaultException> がスローされます。 条件付きの更新メカニズムでは、クライアントからサーバーにリソースのそのエンティティを持っていることを通知し、クライアントが現在のエンティティを持っている場合にのみリソースの変更を許可することができます。 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> メソッドの使用例は、サービスの `UpdateCustomer` 操作および `DeleteCustomer` 操作で確認できます。 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> と同様に、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> の呼び出しは戻らない場合があることに注意してください。 そのため、操作を実装するときは、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> の呼び出しの実行前に、要求が成功することがわかるようにする必要があります。そうすることで、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> の呼び出しがなかった場合でも、成功を示すステータス コードがサービスから返されます。  
  
 このサンプルは、コンソール アプリケーション内で実行される自己ホスト型サービスとクライアントで構成されています。 コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1.  条件付きの Get と Put のサンプルのソリューションを開きます。 サンプルを正しく実行するには、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を起動するときに、管理者として実行する必要があります。 これには、右クリックし、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]アイコンをクリックして選択する**管理者として実行**コンテキスト メニュー。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押してコンソール アプリケーション プロジェクトを実行します。 デバッグを有効にしてこのプロジェクトを実行する場合 (Ctrl キーと F5 キーではなく F5 キーだけを押した場合) は、条件付きの GET および PUT のチェックで例外がスローされるとデバッガーが停止します。 停止した場合、サンプルの実行を続けるには F5 キーを押してください。  
  
3.  コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。  
  
4.  サンプルが実行されると、クライアントは要求をサービスに送信し、応答をコンソール ウィンドウに書き込みます。  
  
5.  任意のキーを押して、サンプルを終了します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\ConditionalGetAndPut`
