---
title: "条件付きの Get と Put | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d22067f-57b8-4e0f-a571-a694512187ae
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 条件付きの Get と Put
このサンプルでは、新しい条件付きの取得 API と更新 API を WCF REST プログラミング モデルで使用する方法を示します。条件付きの取得と更新はリソース指向の REST サービスに最も適しているため、このサンプルでは[基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)のサンプルを拡張します。ここでは、[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] で導入された新しい API を使用して、条件付きの取得と更新のサポートを[基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)のサンプルに追加する方法について説明します。  
  
## 使用例  
 条件付きの取得と更新  
  
## 説明  
 このサンプルの WCF サービスでは、リソース指向の REST 方式で顧客のコレクションが公開されます。サービスの実装の詳細については、「[基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)」のサンプルを参照してください。  
  
 このサンプルでは、条件付きの取得機能と更新機能を[基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)のサンプルに追加します。条件付きの取得と更新では、HTTP のエンティティ タグと HTTP の If\-None\-Match ヘッダーおよび If\-Match ヘッダーを使用して、指定されたリソースの最新のエンティティがクライアントにあるかどうかを検証します。しかし、HTTP の If\-None\-Match ヘッダーと If\-Match ヘッダーを正しく解析するコードを実装することは、面倒であるだけでなく間違いの元にもなります。そのため、<xref:System.ServiceModel.Web.IncomingWebRequestContext> に <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> メソッドと <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> メソッドが追加され、<xref:System.ServiceModel.Web.WebOperationContext> の現在のインスタンスを使用してアクセスできるようになっています。さらに、<xref:System.ServiceModel.Web.OutgoingWebRequestContext> に `SetETag` メソッドが追加されているため、有効なエンティティ タグを返すのも簡単になります。  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> メソッドは、\[WebGet\] 操作で使用されることを想定しています。このメソッドは、指定されたリソースの現在のエンティティ タグを `entityTag` パラメーターとして取得します。これは、`string`、`int`、`long`、または `Guid` のいずれかになります。<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> メソッドは、エンティティ タグを要求の HTTP If\-None\-Match ヘッダーと照合してチェックします。エンティティ タグが HTTP If\-None\-Match ヘッダーにある場合、ステータス コード 304 \(変更なし\) が設定された <xref:System.ServiceModel.Web.WebFaultException> がスローされます。それ以外の場合は、メソッドから制御が戻ります。条件付きの取得メカニズムでは、クライアントからサーバーにそのエンティティを持っていることを通知し、クライアントがまだ現在のエンティティを持っていない場合にのみエンティティを送信することができます。<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> メソッドの使用例は、サービスの `GetCustomer` 操作および `GetCustomers` 操作で確認できます。<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> の呼び出しは戻らない場合があることに注意してください。そのため、操作を実装するときは、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> の呼び出しの実行前に、要求が成功することがわかるようにする必要があります。そうすることで、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> の呼び出しがなかった場合でも、成功を示すステータス コードが設定された応答がサービスから送信されます。  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> メソッドは、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> メソッドに似ています。このメソッドも、指定されたリソースの現在のエンティティ タグを取得します。ただし、このメソッドは、メソッドが "PUT" または "DELETE" に設定された \[WebInvoke\] 操作で使用されることを想定しています。<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> メソッドは、エンティティ タグを要求の HTTP If\-Match ヘッダーと照合してチェックします。エンティティ タグが HTTP If\-Match ヘッダーにない場合、ステータス コード 412 \(必須条件に失敗しました\) が設定された <xref:System.ServiceModel.Web.WebFaultException> がスローされます。条件付きの更新メカニズムでは、クライアントからサーバーにリソースのそのエンティティを持っていることを通知し、クライアントが現在のエンティティを持っている場合にのみリソースの変更を許可することができます。<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> メソッドの使用例は、サービスの `UpdateCustomer` 操作および `DeleteCustomer` 操作で確認できます。<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> と同様に、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> の呼び出しは戻らない場合があることに注意してください。そのため、操作を実装するときは、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> の呼び出しの実行前に、要求が成功することがわかるようにする必要があります。そうすることで、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> の呼び出しがなかった場合でも、成功を示すステータス コードがサービスから返されます。  
  
 このサンプルは、コンソール アプリケーション内で実行される自己ホスト型サービスとクライアントで構成されています。コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。  
  
#### サンプルを実行するには  
  
1.  条件付きの Get と Put のサンプルのソリューションを開きます。サンプルを正しく実行するには、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を起動するときに、管理者として実行する必要があります。管理者として実行するには、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] アイコンを右クリックし、コンテキスト メニューの **\[管理者として実行\]** をクリックします。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押してコンソール アプリケーション プロジェクトを実行します。デバッグを有効にしてこのプロジェクトを実行する場合 \(Ctrl キーと F5 キーではなく F5 キーだけを押した場合\) は、条件付きの GET および PUT のチェックで例外がスローされるとデバッガーが停止します。停止した場合、サンプルの実行を続けるには F5 キーを押してください。  
  
3.  コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。  
  
4.  サンプルが実行されると、クライアントは要求をサービスに送信し、応答をコンソール ウィンドウに書き込みます。  
  
5.  任意のキーを押して、サンプルを終了します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\ConditionalGetAndPut`