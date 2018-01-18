---
title: "チュートリアル : リレーションシップ間でのクエリの実行 (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fef9880d5f9fa652eab2eb0d17bbf782dc64773d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a><span data-ttu-id="634b4-102">チュートリアル : リレーションシップ間でのクエリの実行 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="634b4-102">Walkthrough: Querying Across Relationships (Visual Basic)</span></span>
<span data-ttu-id="634b4-103">このチュートリアルの使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]*アソシエーション*をデータベース内の外部キー リレーションシップを表します。</span><span class="sxs-lookup"><span data-stu-id="634b4-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="634b4-104">このチュートリアルは、Visual Basic 開発設定を使用して記述されています。</span><span class="sxs-lookup"><span data-stu-id="634b4-104">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="634b4-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="634b4-105">Prerequisites</span></span>  
 <span data-ttu-id="634b4-106">完了する必要があります[チュートリアル: 単純なオブジェクト モデルとクエリ (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)です。</span><span class="sxs-lookup"><span data-stu-id="634b4-106">You must have completed [Walkthrough: Simple Object Model and Query (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span></span> <span data-ttu-id="634b4-107">このチュートリアルは前のチュートリアルに基づいて作成されており、c:\linqtest に northwnd.mdf ファイルがあることが前提です。</span><span class="sxs-lookup"><span data-stu-id="634b4-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="634b4-108">概要</span><span class="sxs-lookup"><span data-stu-id="634b4-108">Overview</span></span>  
 <span data-ttu-id="634b4-109">このチュートリアルは、主に次の 3 つの手順で構成されています。</span><span class="sxs-lookup"><span data-stu-id="634b4-109">This walkthrough consists of three main tasks:</span></span>  
  
-   <span data-ttu-id="634b4-110">エンティティ クラスを追加して、Northwind サンプル データベース内の Orders テーブルを表します。</span><span class="sxs-lookup"><span data-stu-id="634b4-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
-   <span data-ttu-id="634b4-111">`Customer` クラスに注釈を付けて、`Customer` クラスと `Order` クラス間のリレーションシップを強化します。</span><span class="sxs-lookup"><span data-stu-id="634b4-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
-   <span data-ttu-id="634b4-112">クエリを作成および実行して、`Order` クラスによる `Customer` 情報の取得のプロセスをテストします。</span><span class="sxs-lookup"><span data-stu-id="634b4-112">Creating and running a query to test the process of obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="634b4-113">テーブル間のリレーションシップを指定する</span><span class="sxs-lookup"><span data-stu-id="634b4-113">Mapping Relationships across Tables</span></span>  
 <span data-ttu-id="634b4-114">`Customer` クラス定義の後に、次のコードから成る `Order` エンティティ クラス定義を作成します。これは、`Orders.Customer` が外部キーとして `Customers.CustomerID` に関係することを示しています。</span><span class="sxs-lookup"><span data-stu-id="634b4-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Orders.Customer` relates as a foreign key to `Customers.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="634b4-115">Order エンティティ クラスを追加するには</span><span class="sxs-lookup"><span data-stu-id="634b4-115">To add the Order entity class</span></span>  
  
-   <span data-ttu-id="634b4-116">`Customer` クラスの後に次のコードを入力または貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="634b4-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="634b4-117">Customer クラスに注釈を付ける</span><span class="sxs-lookup"><span data-stu-id="634b4-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="634b4-118">ここでは、`Customer` クラスに注釈を付けて、`Order` クラスとのリレーションシップを指定します。</span><span class="sxs-lookup"><span data-stu-id="634b4-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="634b4-119">いずれかの方向のリレーションシップが定義されていればリンクを作成できるため、この注釈の追加は必ずしも必要ではありません。</span><span class="sxs-lookup"><span data-stu-id="634b4-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="634b4-120">しかし、この注釈を追加することで、どちらの方向でも簡単にオブジェクトを移動できます。</span><span class="sxs-lookup"><span data-stu-id="634b4-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="634b4-121">Customer クラスに注釈を付けるには</span><span class="sxs-lookup"><span data-stu-id="634b4-121">To annotate the Customer class</span></span>  
  
-   <span data-ttu-id="634b4-122">`Customer` クラスに次のコードを入力または貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="634b4-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="634b4-123">Customer-Order リレーションシップ間のクエリを作成および実行する</span><span class="sxs-lookup"><span data-stu-id="634b4-123">Creating and Running a Query across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="634b4-124">`Order` オブジェクトから `Customer` オブジェクトに、またはその逆の順序で、直接アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="634b4-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="634b4-125">必要としない、明示的な*結合*customers と orders のです。</span><span class="sxs-lookup"><span data-stu-id="634b4-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="634b4-126">Customer オブジェクトを使用して Order オブジェクトにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="634b4-126">To access Order objects by using Customer objects</span></span>  
  
1.  <span data-ttu-id="634b4-127">`Sub Main` メソッドに次のコードを入力または貼り付けることによって、メソッドを変更します。</span><span class="sxs-lookup"><span data-stu-id="634b4-127">Modify the `Sub Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2.  <span data-ttu-id="634b4-128">F5 キーを押して、アプリケーションをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="634b4-128">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="634b4-129">2 つの名前がメッセージ ボックスに表示され、生成された SQL コードがコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="634b4-129">Two names appear in the message box, and the Console window shows the generated SQL code.</span></span>  
  
3.  <span data-ttu-id="634b4-130">メッセージ ボックスを閉じて、デバッグを停止します。</span><span class="sxs-lookup"><span data-stu-id="634b4-130">Close the message box to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="634b4-131">データベースの厳密に型指定されたビューを作成する</span><span class="sxs-lookup"><span data-stu-id="634b4-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="634b4-132">データベースの厳密に型指定されたビューを使用すると、操作が非常に簡単になります。</span><span class="sxs-lookup"><span data-stu-id="634b4-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="634b4-133"><xref:System.Data.Linq.DataContext> オブジェクトを厳密に型指定することによって、<xref:System.Data.Linq.DataContext.GetTable%2A> を呼び出す必要がありません。</span><span class="sxs-lookup"><span data-stu-id="634b4-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="634b4-134">厳密に型指定された <xref:System.Data.Linq.DataContext> オブジェクトを使用する場合は、すべてのクエリで、厳密に型指定されたテーブルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="634b4-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="634b4-135">次の手順では、データベース内の Customers テーブルに対応する厳密に型指定されたテーブルとして、`Customers` を作成します。</span><span class="sxs-lookup"><span data-stu-id="634b4-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="634b4-136">DataContext オブジェクトを厳密に型指定するには</span><span class="sxs-lookup"><span data-stu-id="634b4-136">To strongly type the DataContext object</span></span>  
  
1.  <span data-ttu-id="634b4-137">`Customer` クラス宣言の上に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="634b4-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2.  <span data-ttu-id="634b4-138">`Sub Main` を次のように変更し、厳密に型指定された <xref:System.Data.Linq.DataContext> を使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="634b4-138">Modify `Sub Main` to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3.  <span data-ttu-id="634b4-139">F5 キーを押して、アプリケーションをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="634b4-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="634b4-140">コンソール ウィンドウの出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="634b4-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4.  <span data-ttu-id="634b4-141">コンソール ウィンドウで Enter キーを押してアプリケーションを終了します。</span><span class="sxs-lookup"><span data-stu-id="634b4-141">Press Enter in the Console window to close the application.</span></span>  
  
5.  <span data-ttu-id="634b4-142">**ファイル** メニューのをクリックして**すべて保存**をこのアプリケーションを保存する場合。</span><span class="sxs-lookup"><span data-stu-id="634b4-142">On the **File** menu, click **Save All** if you want to save this application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="634b4-143">次の手順</span><span class="sxs-lookup"><span data-stu-id="634b4-143">Next Steps</span></span>  
 <span data-ttu-id="634b4-144">次のチュートリアル ([チュートリアル: データの操作 (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) データを操作する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="634b4-144">The next walkthrough ([Walkthrough: Manipulating Data (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="634b4-145">そのチュートリアルを実行するのに、既に終了したこのシリーズの 2 つのチュートリアルを保存する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="634b4-145">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="634b4-146">参照</span><span class="sxs-lookup"><span data-stu-id="634b4-146">See Also</span></span>  
 [<span data-ttu-id="634b4-147">チュートリアルによる学習</span><span class="sxs-lookup"><span data-stu-id="634b4-147">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
