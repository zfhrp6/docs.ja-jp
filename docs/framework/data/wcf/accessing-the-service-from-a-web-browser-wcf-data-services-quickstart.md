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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1f6598b1aff20a8b3471ca1ccb59bb5c6576efdc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="59748-102">Web ブラウザーからサービスへのアクセス (WCF Data Services クイックスタート)</span><span class="sxs-lookup"><span data-stu-id="59748-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>
<span data-ttu-id="59748-103">このタスクでは、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] から [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] を開始し、必要に応じて Web ブラウザーでのフィード読み取りを無効にします。</span><span class="sxs-lookup"><span data-stu-id="59748-103">In this task, you will start the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] from [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="59748-104">サービス定義ドキュメントを取得するだけでなく公開されているリソースを Web ブラウザーから HTTP GET 要求を送信することでデータ サービス リソースにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="59748-104">You will then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59748-105">既定では、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] によって、コンピューター上の `localhost` URI にポート番号が自動的に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="59748-105">By default, [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="59748-106">このタスクでは、URI の例でポート番号 `12345` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="59748-106">This task uses the port number `12345` in the URI examples.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="59748-107">特定のポート番号を設定する方法、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]プロジェクトを参照してください[データ サービスの作成](../../../../docs/framework/data/wcf/creating-the-data-service.md)です。</span><span class="sxs-lookup"><span data-stu-id="59748-107"> how to set a specific port number in your [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] project see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
### <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="59748-108">Internet Explorer を使用して既定のサービス ドキュメントを要求するには</span><span class="sxs-lookup"><span data-stu-id="59748-108">To request the default service document by using Internet Explorer</span></span>  
  
1.  <span data-ttu-id="59748-109">Internet Explorer から、**ツール**メニューの [**インターネット オプション**をクリックして、**コンテンツ**] タブで、をクリックして**設定**をオフ**フィードの読み取りビュー オン**です。</span><span class="sxs-lookup"><span data-stu-id="59748-109">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>  
  
     <span data-ttu-id="59748-110">フィードの読み取りが無効になります。</span><span class="sxs-lookup"><span data-stu-id="59748-110">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="59748-111">この機能が無効でなければ、Web ブラウザーは、AtomPub エンコードのドキュメントが返されると生の XML データを表示せずに XML フィードとして処理します。</span><span class="sxs-lookup"><span data-stu-id="59748-111">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59748-112">ブラウザーでフィードを生の XML データとして表示できない場合は、そのままでフィードをページのソース コードとして表示できます。</span><span class="sxs-lookup"><span data-stu-id="59748-112">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>  
  
2.  <span data-ttu-id="59748-113">[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] で F5 キーを押してアプリケーションのデバッグを開始します。</span><span class="sxs-lookup"><span data-stu-id="59748-113">In [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], press the F5 key to start debugging the application.</span></span>  
  
3.  <span data-ttu-id="59748-114">ローカル コンピューターで Web ブラウザーを開きます。</span><span class="sxs-lookup"><span data-stu-id="59748-114">Open a Web browser on the local computer.</span></span> <span data-ttu-id="59748-115">アドレス バーに次の URI を入力します。</span><span class="sxs-lookup"><span data-stu-id="59748-115">In the address bar, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc  
    ```  
  
     <span data-ttu-id="59748-116">既定のサービス ドキュメントが返されます。このドキュメントには、このデータ サービスによって公開されているエンティティ セットの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="59748-116">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>  
  
### <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="59748-117">Web ブラウザーからエンティティ セット リソースにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="59748-117">To access entity set resources from a Web browser</span></span>  
  
1.  <span data-ttu-id="59748-118">Web ブラウザーのアドレス バーに次の URI を入力します。</span><span class="sxs-lookup"><span data-stu-id="59748-118">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers  
    ```  
  
     <span data-ttu-id="59748-119">Northwind サンプル データベース内のすべての顧客のセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="59748-119">This returns a set of all customers in the Northwind sample database.</span></span>  
  
2.  <span data-ttu-id="59748-120">Web ブラウザーのアドレス バーに次の URI を入力します。</span><span class="sxs-lookup"><span data-stu-id="59748-120">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')  
    ```  
  
     <span data-ttu-id="59748-121">特定の顧客 `ALFKI` のエンティティ インスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="59748-121">This returns an entity instance for the specific customer, `ALFKI`.</span></span>  
  
3.  <span data-ttu-id="59748-122">Web ブラウザーのアドレス バーに次の URI を入力します。</span><span class="sxs-lookup"><span data-stu-id="59748-122">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders  
    ```  
  
     <span data-ttu-id="59748-123">顧客と注文の間のリレーションシップがスキャンされ、特定の顧客 `ALFKI` のすべての注文のセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="59748-123">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>  
  
4.  <span data-ttu-id="59748-124">Web ブラウザーのアドレス バーに次の URI を入力します。</span><span class="sxs-lookup"><span data-stu-id="59748-124">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643  
    ```  
  
     <span data-ttu-id="59748-125">特定の顧客 `ALFKI` に属する注文がフィルターされ、指定した `OrderID` 値に基づいた特定の注文だけが返されます。</span><span class="sxs-lookup"><span data-stu-id="59748-125">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="59748-126">次の手順</span><span class="sxs-lookup"><span data-stu-id="59748-126">Next Steps</span></span>  
 <span data-ttu-id="59748-127">ここでは、Web ブラウザーから特定のリソースに対して HTTP GET 要求を発行して [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] にアクセスしました。</span><span class="sxs-lookup"><span data-stu-id="59748-127">You have successfully accessed the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="59748-128">Web ブラウザーを使用すると、リクエストのアドレス構文を試したり、結果を表示したりすることが簡単にできます。</span><span class="sxs-lookup"><span data-stu-id="59748-128">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="59748-129">しかし、一般的に、この方法では運用データ サービスにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="59748-129">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="59748-130">通常、アプリケーションでは、アプリケーション コードまたはスクリプト言語を使用してデータ サービスと対話します。</span><span class="sxs-lookup"><span data-stu-id="59748-130">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="59748-131">次に、クライアント ライブラリを使用して共通言語ランタイム (CLR) オブジェクトと同様にデータ サービス リソースにアクセスするクライアント アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="59748-131">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>  
  
 [<span data-ttu-id="59748-132">.NET Framework クライアント アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="59748-132">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a><span data-ttu-id="59748-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="59748-133">See Also</span></span>  
 [<span data-ttu-id="59748-134">データ サービス リソースへのアクセス</span><span class="sxs-lookup"><span data-stu-id="59748-134">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
