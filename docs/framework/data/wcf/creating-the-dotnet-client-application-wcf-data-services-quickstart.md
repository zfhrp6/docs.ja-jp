---
title: .NET Framework クライアント アプリケーションの作成 (WCF Data Services クイック スタート)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 09981a7aee2db24d8464bbc7412b82a57ec8115b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365356"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>.NET Framework クライアント アプリケーションの作成 (WCF Data Services クイック スタート)
これは、最後のタスク、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]クイック スタート。 このタスクが、コンソール アプリケーションをソリューションに追加されたらへの参照を追加、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]この新しいクライアント、アプリケーションにアクセス フィード、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]生成されたクライアント データ サービス クラスおよびクライアントを使用して、クライアント アプリケーションからフィードライブラリ。  
  
> [!NOTE]
>  データ フィードへのアクセスには .NET Framework ベースのクライアント アプリケーションは必要ありません。 データ サービスは、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを使用する任意のアプリケーション コンポーネントからアクセスできます。 詳細については、次を参照してください。[クライアント アプリケーションでデータ サービスを使用して](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md)です。  
  
### <a name="to-create-the-client-application-by-using-visual-studio"></a>Visual Studio を使用してクライアント アプリケーションを作成するには  
  
1.  **ソリューション エクスプ ローラー**ソリューションを右クリックしをクリックして**追加**、クリックして**新しいプロジェクト**です。  
  
2.  **プロジェクトの種類**をクリックして**Windows**、し、 **WPF アプリケーション**で、**テンプレート**ウィンドウです。  
  
3.  入力`NorthwindClient`プロジェクト名、およびクリック**OK**です。  
  
4.  ファイル MainWindow.xaml を開き、XAML コードを次のコードに置き換えます。  
  
     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]  
  
### <a name="to-add-a-data-service-reference-to-the-project"></a>データ サービス参照をプロジェクトに追加するには  
  
1.  NorthwindClient プロジェクトを右クリックし、をクリックして**サービス参照の追加**、クリックして**Discover**です。  
  
     最初のタスクで作成した Northwind データ サービスが表示されます。  
  
2.  **Namespace**テキスト ボックスで、「 `Northwind`、順にクリック**OK**です。  
  
     プロジェクトに新しいコード ファイルが追加されます。このコード ファイルには、データ サービス リソースにアクセスし、オブジェクトとしてデータ サービス リソースと対話するデータ クラスが含まれています。 データ クラスは、名前空間 `NorthwindClient.Northwind` で作成されます。  
  
### <a name="to-access-data-service-data-in-the-wpf-application"></a>WPF アプリケーションのデータ サービスにアクセスするには  
  
1.  **ソリューション エクスプ ローラー**  **NorthwindClient**プロジェクトを右クリックし、クリックして、**参照の追加**です。  
  
2.  参照の追加 ダイアログ ボックス、 **.NET**  タブ、System.Data.Services.Client.dll アセンブリを選択し、をクリックして**OK**です。 **ソリューション エクスプ ローラー**  **NorthwindClient**MainWindow.xaml ファイルのコード ページを開き、次の追加`using`ステートメント (`Imports` Visual Basic で)。  
  
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
  
### <a name="to-build-and-run-the-northwindclient-application"></a>NorthwindClient アプリケーションをビルドして実行するには  
  
1.  **ソリューション エクスプ ローラー**NorthwindClient プロジェクトを右クリックし、選択、**スタートアップ プロジェクトとして設定**です。  
  
2.  F5 キーを押してアプリケーションを起動します。  
  
     ソリューションがビルドされ、クライアント アプリケーションが起動します。 データがサービスから要求され、コンソールに表示されます。  
  
3.  値を編集、**数量**をクリックし、データ グリッドの列**保存**です。  
  
     変更内容はデータ サービスに保存されます。  
  
    > [!NOTE]
    >  このバージョンの NorthwindClient アプリケーションでは、エンティティの追加と削除はサポートされません。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、サンプル Northwind の [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードにアクセスするクライアント アプリケーションを作成しました。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クイック スタートも完了しました。 アクセスの詳細については、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]からフィード、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アプリケーションを参照してください[WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)です。  
  
## <a name="see-also"></a>関連項目  
 [はじめに](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [リソース](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
