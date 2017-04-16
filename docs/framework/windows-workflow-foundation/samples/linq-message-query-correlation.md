---
title: "LINQ メッセージ クエリの関連付け | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# LINQ メッセージ クエリの関連付け
このサンプルでは、システム標準の <xref:System.ServiceModel.XPathMessageQuery> ではなく、カスタムの <xref:System.ServiceModel.Dispatcher.MessageQuery> 実装を使用して、コンテンツ ベースの関連付けを実行する方法を示します。  
  
## 使用例  
 カスタムの <xref:System.ServiceModel.Dispatcher.MessageQuery>、コンテンツ ベースの相関関係。  
  
## 説明  
 このサンプルでは、関連付けのために <xref:System.ServiceModel.Dispatcher.MessageQuery> 基本クラスから拡張する方法を示します。カスタム実装の `LinqMessageQuery` を使用すると、XLinq を使用してメッセージ内で検索する XName を指定できます。クエリによって取得されたデータを使用して、メッセージを適切なワークフロー インスタンスにディスパッチするための相関関係キーを作成します。  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  このサンプルでは、HTTP エンドポイントを使用してワークフロー サービスを公開します。このサンプルを実行するには、適切な URL ACL を追加する必要があります \(詳細については、「[HTTP および HTTPS の構成](http://go.microsoft.com/fwlink/?LinkId=70353)」を参照\)。適切な ACL を追加するには、Visual Studio を管理者として実行するか、権限のレベルが高いプロンプトで次のコマンドを実行します。ドメインとユーザー名は置き換えてください。  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  URL ACL を追加したら、次の手順を実行します。  
  
    1.  ソリューションをビルドします。  
  
    2.  ソリューションを右クリックし、**\[スタートアップ プロジェクトの設定\]** をクリックして、複数のスタートアップ プロジェクトを設定します。複数のスタートアップ プロジェクトとして **Service** および **Client** を \(この順序で\) 追加します。  
  
    3.  アプリケーションを実行します。クライアント コンソールには、注文を送信し、発注書 ID を受信した後に、注文を確認するワークフローが示されます。Service のウィンドウには、処理されている要求が示されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`