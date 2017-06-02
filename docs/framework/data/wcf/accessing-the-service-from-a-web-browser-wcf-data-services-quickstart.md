---
title: "Web ブラウザーからサービスへのアクセス (WCF Data Services クイックスタート) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Web ブラウザーからサービスへのアクセス (WCF Data Services クイックスタート)
このタスクでは、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] から [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を開始し、必要に応じて Web ブラウザーでのフィード読み取りを無効にします。  次に、公開されているリソースに対して Web ブラウザーから HTTP GET 要求を送信し、サービス定義ドキュメントを取得して、データ サービス リソースにアクセスします。  
  
> [!NOTE]
>  既定では、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] によって、コンピューター上の `localhost` URI にポート番号が自動的に割り当てられます。  このタスクでは、URI の例でポート番号 `12345` を使用しています。  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] プロジェクトの指定のポート番号をセットする方法は、「[データ サービスの作成](../../../../docs/framework/data/wcf/creating-the-data-service.md)」を参照してください。  
  
### Internet Explorer を使用して既定のサービス ドキュメントを要求するには  
  
1.  Internet Explorer の **\[ツール\]** メニューので **\[インターネット オプション\]** をクリックし、**\[コンテンツ\]** タブの **\[設定\]** をクリックして **\[フィードの読み取りビューを有効にする\]** をオフにします。  
  
     フィードの読み取りが無効になります。  この機能が無効でなければ、Web ブラウザーは、AtomPub エンコードのドキュメントが返されると生の XML データを表示せずに XML フィードとして処理します。  
  
    > [!NOTE]
    >  ブラウザーでフィードを生の XML データとして表示できない場合は、そのままでフィードをページのソース コードとして表示できます。  
  
2.  [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] で F5 キーを押してアプリケーションのデバッグを開始します。  
  
3.  ローカル コンピューターで Web ブラウザーを開きます。  アドレス バーに次の URI を入力します。  
  
    ```  
    http://localhost:12345/northwind.svc  
    ```  
  
     既定のサービス ドキュメントが返されます。このドキュメントには、このデータ サービスによって公開されているエンティティ セットの一覧が含まれています。  
  
### Web ブラウザーからエンティティ セット リソースにアクセスするには  
  
1.  Web ブラウザーのアドレス バーに次の URI を入力します。  
  
    ```  
    http://localhost:12345/northwind.svc/Customers  
    ```  
  
     Northwind サンプル データベース内のすべての顧客のセットが返されます。  
  
2.  Web ブラウザーのアドレス バーに次の URI を入力します。  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')  
    ```  
  
     特定の顧客 `ALFKI` のエンティティ インスタンスが返されます。  
  
3.  Web ブラウザーのアドレス バーに次の URI を入力します。  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders  
    ```  
  
     顧客と注文の間のリレーションシップがスキャンされ、特定の顧客 `ALFKI` のすべての注文のセットが返されます。  
  
4.  Web ブラウザーのアドレス バーに次の URI を入力します。  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643  
    ```  
  
     特定の顧客 `ALFKI` に属する注文がフィルターされ、指定した `OrderID` 値に基づいた特定の注文だけが返されます。  
  
## 次の手順  
 ここでは、Web ブラウザーから特定のリソースに対して HTTP GET 要求を発行して [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] にアクセスしました。  Web ブラウザーを使用すると、リクエストのアドレス構文を試したり、結果を表示したりすることが簡単にできます。  しかし、一般的に、この方法では運用データ サービスにはアクセスできません。  通常、アプリケーションは、アプリケーション コードまたはスクリプト言語を通し、データ サービスと対話します。次に、共通言語ランタイム \(CLR\) オブジェクトのように、クライアント ライブラリを使用してデータ サービス リソースにアクセスするクライアント アプリケーションを作成します。  
  
 [.NET Framework クライアント アプリケーションの作成](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
  
## 参照  
 [データ サービス リソースへのアクセス](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)