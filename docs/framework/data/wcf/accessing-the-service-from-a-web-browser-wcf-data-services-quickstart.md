---
title: "Web ブラウザーからサービスへのアクセス (WCF Data Services クイックスタート)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 49deb2e209127f92a333195e9fcd0d1e1bece7d8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a>Web ブラウザーからサービスへのアクセス (WCF Data Services クイックスタート)
このタスクでは、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] から [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] を開始し、必要に応じて Web ブラウザーでのフィード読み取りを無効にします。 サービス定義ドキュメントを取得するだけでなく公開されているリソースを Web ブラウザーから HTTP GET 要求を送信することでデータ サービス リソースにアクセスします。  
  
> [!NOTE]
>  既定では、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] によって、コンピューター上の `localhost` URI にポート番号が自動的に割り当てられます。 このタスクでは、URI の例でポート番号 `12345` を使用しています。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]特定のポート番号を設定する方法、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]プロジェクトを参照してください[データ サービスの作成](../../../../docs/framework/data/wcf/creating-the-data-service.md)です。  
  
### <a name="to-request-the-default-service-document-by-using-internet-explorer"></a>Internet Explorer を使用して既定のサービス ドキュメントを要求するには  
  
1.  Internet Explorer から、**ツール**メニューの [**インターネット オプション**をクリックして、**コンテンツ**] タブで、をクリックして**設定**をオフ**フィードの読み取りビュー オン**です。  
  
     フィードの読み取りが無効になります。 この機能が無効でなければ、Web ブラウザーは、AtomPub エンコードのドキュメントが返されると生の XML データを表示せずに XML フィードとして処理します。  
  
    > [!NOTE]
    >  ブラウザーでフィードを生の XML データとして表示できない場合は、そのままでフィードをページのソース コードとして表示できます。  
  
2.  [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] で F5 キーを押してアプリケーションのデバッグを開始します。  
  
3.  ローカル コンピューターで Web ブラウザーを開きます。 アドレス バーに次の URI を入力します。  
  
    ```  
    http://localhost:12345/northwind.svc  
    ```  
  
     既定のサービス ドキュメントが返されます。このドキュメントには、このデータ サービスによって公開されているエンティティ セットの一覧が含まれています。  
  
### <a name="to-access-entity-set-resources-from-a-web-browser"></a>Web ブラウザーからエンティティ セット リソースにアクセスするには  
  
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
  
## <a name="next-steps"></a>次の手順  
 ここでは、Web ブラウザーから特定のリソースに対して HTTP GET 要求を発行して [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] にアクセスしました。 Web ブラウザーを使用すると、リクエストのアドレス構文を試したり、結果を表示したりすることが簡単にできます。 しかし、一般的に、この方法では運用データ サービスにはアクセスできません。 通常、アプリケーションでは、アプリケーション コードまたはスクリプト言語を使用してデータ サービスと対話します。 次に、クライアント ライブラリを使用して共通言語ランタイム (CLR) オブジェクトと同様にデータ サービス リソースにアクセスするクライアント アプリケーションを作成します。  
  
 [.NET Framework クライアント アプリケーションの作成](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a>関連項目  
 [データ サービス リソースへのアクセス](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
