---
title: ".NET Framework クライアント アプリケーションの作成 (WCF Data Services クイック スタート) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# .NET Framework クライアント アプリケーションの作成 (WCF Data Services クイック スタート)
これは、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クイック スタートの最後のタスクです。  このタスクでは、コンソール アプリケーションをソリューションに追加し、この新しいクライアント アプリケーションに [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] フィードへの参照を追加します。次に、生成されたクライアント データ サービス クラスおよびクライアント ライブラリを使用して、クライアント アプリケーションから [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードにアクセスします。  
  
> [!NOTE]
>  データ フィードへのアクセスには .NET Framework ベースのクライアント アプリケーションは必要ありません。  データ サービスは、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを使用する任意のアプリケーション コンポーネントからアクセスできます。  詳細については、「[クライアント アプリケーションでのデータ サービスの使用](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md)」を参照してください。  
  
### Visual Studio を使用してクライアント アプリケーションを作成するには  
  
1.  **ソリューション エクスプローラー**でソリューションを右クリックし、**\[追加\]** をポイントして **\[新しいプロジェクト\]** をクリックします。  
  
2.  **\[プロジェクトの種類\]** で **\[Windows\]** をクリックして、**\[テンプレート\]** ペインで **\[WPF アプリケーション\]** を選択します。  
  
3.  プロジェクト名として「`NorthwindClient`」を入力し、**\[OK\]** をクリックします。  
  
4.  ファイル MainWindow.xaml を開き、XAML コードを次のコードに置き換えます。  
  
     [!code-xml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]  
  
### データ サービス参照をプロジェクトに追加するには  
  
1.  NorthwindClient プロジェクトを右クリックして、**\[サービス参照の追加\]**、**\[探索\]** の順にクリックします。  
  
     最初のタスクで作成した Northwind データ サービスが表示されます。  
  
2.  **\[名前空間\]** ボックスに「`Northwind`」と入力し、**\[OK\]** をクリックします。  
  
     プロジェクトに新しいコード ファイルが追加されます。このコード ファイルには、データ サービス リソースにアクセスし、オブジェクトとしてデータ サービス リソースと対話するデータ クラスが含まれています。  データ クラスは、名前空間 `NorthwindClient.Northwind` で作成されます。  
  
### WPF アプリケーションのデータ サービスにアクセスするには  
  
1.  **NorthwindClient** の下の**ソリューション エクスプローラー**でプロジェクトを右クリックして、**\[参照の追加\]** をクリックします。  
  
2.  \[参照の追加\] ダイアログ ボックスで、**\[.NET\]** タブをクリックし、System.Data.Services.Client.dll アセンブリを選択して、**\[OK\]** をクリックします。  **NorthwindClient** の下の**ソリューション エクスプローラー**で、MainWindow.xaml ファイルのコード ページを開き、次の `using` ステートメント \(Visual Basic の場合は `Imports`\) を追加します。  
  
     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]  
  
3.  次のコードを挿入します。このコードは、データ サービスをクエリし、<xref:System.Data.Services.Client.DataServiceCollection%601> に対する結果を `MainWindow` クラスにバインドします。  
  
    > [!NOTE]
    >  ホスト名 `localhost:12345` を Northwind データ サービスのインスタンスをホストするサーバーとポートで置き換えます。  
  
     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]  
  
4.  次のコードを挿入します。このコードは、変更内容を `MainWindow` クラスに保存します。  
  
     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]  
  
### NorthwindClient アプリケーションをビルドして実行するには  
  
1.  **ソリューション エクスプローラー**で NorthwindClient プロジェクトを右クリックして **\[スタートアップ プロジェクトに設定\]** を選択します。  
  
2.  F5 キーを押してアプリケーションを起動します。  
  
     ソリューションがビルドされ、クライアント アプリケーションが起動します。  データがサービスから要求され、コンソールに表示されます。  
  
3.  データ グリッドの **Quantity** 列の値を編集し、**\[保存\]** をクリックします。  
  
     変更内容はデータ サービスに保存されます。  
  
    > [!NOTE]
    >  このバージョンの NorthwindClient アプリケーションでは、エンティティの追加と削除はサポートされません。  
  
## 次の手順  
 ここでは、サンプル Northwind の [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードにアクセスするクライアント アプリケーションを作成しました。  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クイック スタートも完了しました。  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アプリケーションから [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードへのアクセスについては、「[WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)」を参照してください。  
  
## 参照  
 [概要](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)   
 [リソース](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)