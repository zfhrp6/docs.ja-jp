---
title: ASP.NET アプリケーションでの SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 51df8ad695b3e59b368499d35ac76cc7ac0cd6e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sqldependency-in-an-aspnet-application"></a><span data-ttu-id="6fce6-102">ASP.NET アプリケーションでの SqlDependency</span><span class="sxs-lookup"><span data-stu-id="6fce6-102">SqlDependency in an ASP.NET Application</span></span>
<span data-ttu-id="6fce6-103">ここでは、ASP.NET の <xref:System.Data.SqlClient.SqlDependency> オブジェクトを使用して、<xref:System.Web.Caching.SqlCacheDependency> を間接的に使用する方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="6fce6-103">The example in this section shows how to use <xref:System.Data.SqlClient.SqlDependency> indirectly by leveraging the ASP.NET <xref:System.Web.Caching.SqlCacheDependency> object.</span></span> <span data-ttu-id="6fce6-104"><xref:System.Web.Caching.SqlCacheDependency> オブジェクトでは <xref:System.Data.SqlClient.SqlDependency> を使用して通知をリッスンし、キャッシュを適切に更新します。</span><span class="sxs-lookup"><span data-stu-id="6fce6-104">The <xref:System.Web.Caching.SqlCacheDependency> object uses a <xref:System.Data.SqlClient.SqlDependency> to listen for notifications and correctly update the cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6fce6-105">サンプル コードは、内のスクリプトを実行することによって、クエリ通知を有効にした前提としています。[クエリ通知の有効化](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)です。</span><span class="sxs-lookup"><span data-stu-id="6fce6-105">The sample code assumes that you have enabled query notifications by executing the scripts in [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span></span>  
  
## <a name="about-the-sample-application"></a><span data-ttu-id="6fce6-106">サンプル アプリケーションについて</span><span class="sxs-lookup"><span data-stu-id="6fce6-106">About the Sample Application</span></span>  
 <span data-ttu-id="6fce6-107">サンプル アプリケーションでは、単一の ASP.NET Web ページを使用して、製品情報を表示、 **AdventureWorks**で SQL Server データベース、<xref:System.Web.UI.WebControls.GridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="6fce6-107">The sample application uses a single ASP.NET Web page to display product information from the **AdventureWorks** SQL Server database in a <xref:System.Web.UI.WebControls.GridView> control.</span></span> <span data-ttu-id="6fce6-108">ページが読み込まれる際に、<xref:System.Web.UI.WebControls.Label> コントロールに現在の時刻が入力されます。</span><span class="sxs-lookup"><span data-stu-id="6fce6-108">When the page loads, the code writes the current time to a <xref:System.Web.UI.WebControls.Label> control.</span></span> <span data-ttu-id="6fce6-109">次に、<xref:System.Web.Caching.SqlCacheDependency> オブジェクトを定義し、最長 3 分間キャッシュ データを格納するように <xref:System.Web.Caching.Cache> オブジェクトのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="6fce6-109">It then defines a <xref:System.Web.Caching.SqlCacheDependency> object and sets properties on the <xref:System.Web.Caching.Cache> object to store the cache data for up to three minutes.</span></span> <span data-ttu-id="6fce6-110">その後、データベースに接続し、データを取得します。</span><span class="sxs-lookup"><span data-stu-id="6fce6-110">The code then connects to the database and retrieves the data.</span></span> <span data-ttu-id="6fce6-111">ページが読み込まれ、アプリケーションが実行されると、ASP.NET ではキャッシュからデータが取得されます。これは、ページ上の時刻が変更されないことで確認できます。</span><span class="sxs-lookup"><span data-stu-id="6fce6-111">When the page is loaded and the application is running ASP.NET will retrieve data from the cache, which you can verify by noting that the time on the page does not change.</span></span> <span data-ttu-id="6fce6-112">監視しているデータが変化すると、ASP.NET によりキャッシュが無効化され、`GridView` コントロールに最新データが再入力されることで、`Label` コントロールに表示される時刻が更新されます。</span><span class="sxs-lookup"><span data-stu-id="6fce6-112">If the data being monitored changes, ASP.NET invalidates the cache and repopulate the `GridView` control with fresh data, updating the time displayed in the `Label` control.</span></span>  
  
## <a name="creating-the-sample-application"></a><span data-ttu-id="6fce6-113">サンプル アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="6fce6-113">Creating the Sample Application</span></span>  
 <span data-ttu-id="6fce6-114">サンプル アプリケーションを作成して実行するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6fce6-114">Follow these steps to create and run the sample application:</span></span>  
  
1.  <span data-ttu-id="6fce6-115">新しい ASP.NET Web サイトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6fce6-115">Create a new ASP.NET Web site.</span></span>  
  
2.  <span data-ttu-id="6fce6-116">Default.aspx ページに <xref:System.Web.UI.WebControls.Label> コントロールと <xref:System.Web.UI.WebControls.GridView> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="6fce6-116">Add a <xref:System.Web.UI.WebControls.Label> and a <xref:System.Web.UI.WebControls.GridView> control to the Default.aspx page.</span></span>  
  
3.  <span data-ttu-id="6fce6-117">ページのクラス モジュールを開き、次のディレクティブを追加します。</span><span class="sxs-lookup"><span data-stu-id="6fce6-117">Open the page's class module and add the following directives:</span></span>  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4.  <span data-ttu-id="6fce6-118">ページの `Page_Load` イベントに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="6fce6-118">Add the following code in the page's `Page_Load` event:</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5.  <span data-ttu-id="6fce6-119">`GetConnectionString` および `GetSQL` という 2 つのヘルパー メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="6fce6-119">Add two helper methods, `GetConnectionString` and `GetSQL`.</span></span> <span data-ttu-id="6fce6-120">定義される接続文字列は、統合セキュリティを利用します。</span><span class="sxs-lookup"><span data-stu-id="6fce6-120">The connection string defined uses integrated security.</span></span> <span data-ttu-id="6fce6-121">使用しているアカウントと必要なデータベース アクセス許可があることを確認する必要があります、サンプル データベース**AdventureWorks**が有効になっている通知します。</span><span class="sxs-lookup"><span data-stu-id="6fce6-121">You will need to verify that the account you are using has the necessary database permissions and that the sample database, **AdventureWorks**, has notifications enabled.</span></span> <span data-ttu-id="6fce6-122">詳細については、次を参照してください。[特別な考慮事項とを使用してクエリ通知](http://msdn.microsoft.com/library/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7)です。</span><span class="sxs-lookup"><span data-stu-id="6fce6-122">For more information, see [Special Considerations When Using Query Notifications](http://msdn.microsoft.com/library/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7).</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a><span data-ttu-id="6fce6-123">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="6fce6-123">Testing the Application</span></span>  
 <span data-ttu-id="6fce6-124">このアプリケーションは Web フォームに表示されるデータをキャッシングし、操作が行われなければ 3 分ごとにデータを更新します。</span><span class="sxs-lookup"><span data-stu-id="6fce6-124">The application caches the data displayed on the Web form and refreshes it every three minutes if there is no activity.</span></span> <span data-ttu-id="6fce6-125">データベースに変化があれば、キャッシュは直ちに更新されます。</span><span class="sxs-lookup"><span data-stu-id="6fce6-125">If a change occurs to the database, the cache is refreshed immediately.</span></span> <span data-ttu-id="6fce6-126">Visual Studio からアプリケーションを実行すると、ブラウザーにページが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="6fce6-126">Run the application from Visual Studio, which loads the page into the browser.</span></span> <span data-ttu-id="6fce6-127">表示されるキャッシュ更新時刻は、最後にキャッシュが更新された時刻を示します。</span><span class="sxs-lookup"><span data-stu-id="6fce6-127">The cache refresh time displayed indicates when the cache was last refreshed.</span></span> <span data-ttu-id="6fce6-128">3 分間の待機後、ページを更新し、ポストバック イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="6fce6-128">Wait three minutes, and then refresh the page, causing a postback event to occur.</span></span> <span data-ttu-id="6fce6-129">ページに表示される時刻が変更されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6fce6-129">Note that the time displayed on the page has changed.</span></span> <span data-ttu-id="6fce6-130">3 分経過する前にページを更新した場合は、ページに表示される時刻は変わりません。</span><span class="sxs-lookup"><span data-stu-id="6fce6-130">If you refresh the page in less than three minutes, the time displayed on the page will remain the same.</span></span>  
  
 <span data-ttu-id="6fce6-131">次に、Transact-SQL の UPDATE コマンドを使用して、データベースのデータを更新し、ページを更新します。</span><span class="sxs-lookup"><span data-stu-id="6fce6-131">Now update the data in the database, using a Transact-SQL UPDATE command and refresh the page.</span></span> <span data-ttu-id="6fce6-132">表示される時刻を見ると、データベースの新しいデータを使ってキャッシュが更新されたことがわかります。</span><span class="sxs-lookup"><span data-stu-id="6fce6-132">The time displayed now indicates that the cache was refreshed with the new data from the database.</span></span> <span data-ttu-id="6fce6-133">キャッシュは更新されますが、ページに表示される時刻はポストバック イベントが発生するまで変更されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6fce6-133">Note that although the cache is updated, the time displayed on the page does not change until a postback event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fce6-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="6fce6-134">See Also</span></span>  
 [<span data-ttu-id="6fce6-135">SQL Server のクエリ通知</span><span class="sxs-lookup"><span data-stu-id="6fce6-135">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="6fce6-136">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="6fce6-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
