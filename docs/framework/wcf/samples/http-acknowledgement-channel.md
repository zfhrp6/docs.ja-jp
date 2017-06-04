---
title: "HTTP 受信確認チャネル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 469f3056-5ef2-4753-8acf-b574d23d83cf
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# HTTP 受信確認チャネル
HTTP 受信確認チャネルは、一方向メッセージング パターンを変える階層チャネルの例です。これにより、サービスでは、受信確認を自動的に送信するのではなく受信メッセージを承認または拒否できるようになります。また、HTTP 受信確認チャネルにより、サービスでは、メッセージが処理されるというビジネス レベルの保証がなされるまで受信確認を遅らせることができます。  
  
## 使用例  
 <xref:System.ServiceModel.Channels.ReceiveContext>、階層チャネルの例 \(HTTP 受信確認チャネル\)。  
  
## 説明  
 HTTP 受信確認チャネルでは、<xref:System.ServiceModel.Channels.ReceiveContext> を実装して、HTTP 要求\/応答メッセージング パターンを、受信確認の遅延が可能な一方向のパターンに変えます。この新しいパターンを使用すると、サービスでは、OK を示す HTTP ステータス コード 200 の形式で受信確認を送信することによって、メッセージ処理が完了するまでクライアントをブロックすることなく、メッセージ処理を保証できます。または、内部サーバー エラーを示す HTTP ステータス コード 500 の形式でエラー メッセージをクライアントに送信できます。たとえば、サービスでは、メッセージをキューに書き込んだ後に受信確認を送信し、その後で、非同期にメッセージの処理を継続することもできます。このシナリオでは、クライアントは、サービスから受信確認を受け取るまで各メッセージを再送信する場合に、サービスによってメッセージが少なくとも一度は処理されたことを確認できます。ただし、サービスで、メッセージ処理の保証なしに、HTTP を介した非同期の高速なメッセージ処理を行う必要がある場合は、<xref:System.ServiceModel.Channels.OneWayBindingElement> の方が適しています。  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> を使用すると、サービスでメッセージを処理できるかどうか判断している間、メッセージをそのままの状態にしておくことができます。サービスでメッセージを正常に処理できることは、HTTP OK ステータス コードを送信する <xref:System.ServiceModel.Channels.ReceiveContext> オブジェクトで Complete を呼び出すことによって示されます。また、サービスでメッセージを処理できるかどうかは、HTTP 内部サーバー エラー ステータス コードを送信する <xref:System.ServiceModel.Channels.ReceiveContext> オブジェクトで <xref:System.ServiceModel.Channels.ReceiveContext> の `Abandon` メソッドを呼び出すことによって示されます。  
  
 この例では、クライアントは従業員 ID を送信して処理情報を要求します。サービス側では、受信した従業員 ID が 50 を超える場合は、HTTP ステータス コード 500 \(内部サーバー エラー\) をクライアントに送信します。それ以外の場合は、処理を正常に実行できると想定し、HTTP ステータス コード 200 \(成功\) をクライアントに送信します。  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を管理者権限で開きます。  
  
2.  **HttpAckChannel** ソリューションを開きます。  
  
3.  **ソリューション エクスプローラー**で **Service** プロジェクトを右クリックしてプロジェクトの新しいインスタンスを開始し、コンテキスト メニューから **\[デバッグ\]**、**\[新しいインスタンスを開始\]** の順にクリックします。  
  
4.  **ソリューション エクスプローラー**で **Client** プロジェクトを右クリックしてプロジェクトの新しいインスタンスを開始し、コンテキスト メニューから **\[デバッグ\]**、**\[新しいインスタンスを開始\]** の順にクリックします。  
  
5.  サービスが開始されたら、クライアント ウィンドウで Enter キーを押して、クライアントからサービスにメッセージを送信します。  
  
6.  最初のメッセージがサービスで処理され、サービスからクライアントに HTTP OK ステータス コードが送信されます。  
  
7.  2 番目のメッセージは失敗し、サービスからクライアントに HTTP 内部サーバー エラー ステータス コードが送信されます。これにより、<xref:System.ServiceModel.CommunicationException> がクライアントで発生します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpAckChannel`