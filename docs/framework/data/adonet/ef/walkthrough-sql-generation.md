---
title: 'チュートリアル: SQL 生成'
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: ab08b404dc60483a39e5c6ae56d82b63932c3f3e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="walkthrough-sql-generation"></a><span data-ttu-id="7fed2-102">チュートリアル: SQL 生成</span><span class="sxs-lookup"><span data-stu-id="7fed2-102">Walkthrough: SQL Generation</span></span>
<span data-ttu-id="7fed2-103">このトピックでの SQL 生成の実行方法について説明します、[サンプル プロバイダー](http://go.microsoft.com/fwlink/?LinkId=180616)です。</span><span class="sxs-lookup"><span data-stu-id="7fed2-103">This topic illustrates how SQL generation occurs in the [Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616).</span></span> <span data-ttu-id="7fed2-104">次の Entity SQL クエリでは、サンプル プロバイダーに含まれているモデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="7fed2-104">The following Entity SQL query uses the model that is included with the sample provider:</span></span>  
  
```  
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId  
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName  
        FROM NorthwindEntities.Products AS P) as j1  
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry  
            FROM NorthwindEntities.OrderDetails AS OD) as j2  
            ON j1.ProductId == j2.ProductId   
```  
  
 <span data-ttu-id="7fed2-105">このクエリでは、プロバイダーに渡される次の出力コマンド ツリーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-105">The query produces the following output command tree that is passed to the provider:</span></span>  
  
```  
DbQueryCommandTree  
|_Parameters  
|_Query : Collection{Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]}  
  |_Project  
    |_Input : 'Join4'  
    | |_InnerJoin  
    |   |_Left : 'Join1'  
    |   | |_LeftOuterJoin  
    |   |   |_Left : 'Extent1'  
    |   |   | |_Scan : dbo.Products  
    |   |   |_Right : 'Extent2'  
    |   |   | |_Scan : dbo.Categories  
    |   |   |_JoinCondition  
    |   |     |_  
    |   |       |_Var(Extent1).CategoryID  
    |   |       |_=  
    |   |       |_Var(Extent2).CategoryID  
    |   |_Right : 'Join3'  
    |   | |_LeftOuterJoin  
    |   |   |_Left : 'Extent3'  
    |   |   | |_Scan : dbo.OrderDetails  
    |   |   |_Right : 'Join2'  
    |   |   | |_LeftOuterJoin  
    |   |   |   |_Left : 'Extent4'  
    |   |   |   | |_Scan : dbo.Orders  
    |   |   |   |_Right : 'Extent5'  
    |   |   |   | |_Scan : dbo.InternationalOrders  
    |   |   |   |_JoinCondition  
    |   |   |     |_  
    |   |   |       |_Var(Extent4).OrderID  
    |   |   |       |_=  
    |   |   |       |_Var(Extent5).OrderID  
    |   |   |_JoinCondition  
    |   |     |_  
    |   |       |_Var(Extent3).OrderID  
    |   |       |_=  
    |   |       |_Var(Join2).Extent4.OrderID  
    |   |_JoinCondition  
    |     |_  
    |       |_Var(Join1).Extent1.ProductID  
    |       |_=  
    |       |_Var(Join3).Extent3.ProductID  
    |_Projection  
      |_NewInstance : Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]  
        |_Column : 'C1'  
        | |_1  
        |_Column : 'ProductID'  
        | |_Var(Join4).Join1.Extent1.ProductID  
        |_Column : 'ProductName'  
        | |_Var(Join4).Join1.Extent1.ProductName  
        |_Column : 'CategoryName'  
        | |_Var(Join4).Join1.Extent2.CategoryName  
        |_Column : 'ShipCountry'  
        | |_Var(Join4).Join3.Join2.Extent4.ShipCountry  
        |_Column : 'ProductID1'  
          |_Var(Join4).Join3.Extent3.ProductID  
```  
  
 <span data-ttu-id="7fed2-106">このトピックでは、この出力コマンド ツリーを次の SQL ステートメントに変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7fed2-106">This topic describes how to translate this output command tree into the following SQL statements.</span></span>  
  
```  
SELECT   
1 AS [C1],   
[Extent1].[ProductID] AS [ProductID],   
[Extent1].[ProductName] AS [ProductName],   
[Extent2].[CategoryName] AS [CategoryName],   
[Join3].[ShipCountry] AS [ShipCountry],   
[Join3].[ProductID] AS [ProductID1]  
FROM   [dbo].[Products] AS [Extent1]  
LEFT OUTER JOIN [dbo].[Categories] AS [Extent2] ON [Extent1].[CategoryID] = [Extent2].[CategoryID]  
INNER JOIN    
(SELECT [Extent3].[OrderID] AS [OrderID1], [Extent3].[ProductID] AS [ProductID], [Extent3].[UnitPrice] AS [UnitPrice], [Extent3].[Quantity] AS [Quantity], [Extent3].[Discount] AS [Discount], [Join2].[OrderID2], [Join2].[CustomerID], [Join2].[EmployeeID], [Join2].[OrderDate], [Join2].[RequiredDate], [Join2].[ShippedDate], [Join2].[Freight], [Join2].[ShipName], [Join2].[ShipAddress], [Join2].[ShipCity], [Join2].[ShipRegion], [Join2].[ShipPostalCode], [Join2].[ShipCountry], [Join2].[OrderID3], [Join2].[CustomsDescription], [Join2].[ExciseTax]  
FROM  [dbo].[OrderDetails] AS [Extent3]  
LEFT OUTER JOIN    
      (SELECT [Extent4].[OrderID] AS [OrderID2], [Extent4].[CustomerID] AS [CustomerID], [Extent4].[EmployeeID] AS [EmployeeID], [Extent4].[OrderDate] AS [OrderDate], [Extent4].[RequiredDate] AS [RequiredDate], [Extent4].[ShippedDate] AS [ShippedDate], [Extent4].[Freight] AS [Freight], [Extent4].[ShipName] AS [ShipName], [Extent4].[ShipAddress] AS [ShipAddress], [Extent4].[ShipCity] AS [ShipCity], [Extent4].[ShipRegion] AS [ShipRegion], [Extent4].[ShipPostalCode] AS [ShipPostalCode], [Extent4].[ShipCountry] AS [ShipCountry], [Extent5].[OrderID] AS [OrderID3], [Extent5].[CustomsDescription] AS [CustomsDescription], [Extent5].[ExciseTax] AS [ExciseTax]  
FROM  [dbo].[Orders] AS [Extent4]  
LEFT OUTER JOIN [dbo].[InternationalOrders] AS [Extent5] ON [Extent4].[OrderID] = [Extent5].[OrderID]   
      ) AS [Join2] ON [Extent3].[OrderID] = [Join2].[OrderID2]   
   ) AS [Join3] ON [Extent1].[ProductID] = [Join3].[ProductID]  
```  
  
## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="7fed2-107">SQL 生成の最初のフェーズ: 式ツリーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="7fed2-107">First Phase of SQL Generation: Visiting the Expression Tree</span></span>  
 <span data-ttu-id="7fed2-108">次の図は、ビジターの最初の空の状態を示しています。</span><span class="sxs-lookup"><span data-stu-id="7fed2-108">The following figure illustrates the initial empty state of the visitor.</span></span>  <span data-ttu-id="7fed2-109">このトピック全体では、このチュートリアルの説明に関連するプロパティのみを示しています。</span><span class="sxs-lookup"><span data-stu-id="7fed2-109">Throughout this topic, only the properties relevant to the walkthrough explanation are shown.</span></span>  
  
 <span data-ttu-id="7fed2-110">![ダイアグラム](../../../../../docs/framework/data/adonet/ef/media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span><span class="sxs-lookup"><span data-stu-id="7fed2-110">![Diagram](../../../../../docs/framework/data/adonet/ef/media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span></span>  
  
 <span data-ttu-id="7fed2-111">Project ノードにアクセスすると、VisitInputExpression がその入力 (Join4) に対して呼び出され、VisitJoinExpression メソッドによって Join4 のアクセスがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-111">When the Project  node is visited, VisitInputExpression is called over its input (Join4), which triggers the visit of Join4 by the method VisitJoinExpression.</span></span> <span data-ttu-id="7fed2-112">これは最上位の結合であるため、IsParentAJoin は false を返し、新しい SqlSelectStatement (SelectStatement0) が作成され、SELECT ステートメント スタックにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-112">Because this is a topmost join, IsParentAJoin returns false and a new SqlSelectStatement (SelectStatement0) is created and pushed on the SELECT statement stack.</span></span> <span data-ttu-id="7fed2-113">また、新しいスコープ (scope0) がシンボル テーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-113">Also, a new scope (scope0) is entered in the symbol table.</span></span> <span data-ttu-id="7fed2-114">結合の最初の入力 (左辺) にアクセスする前に、'true' が IsParentAJoin スタックにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-114">Before the first (left) input of the join is visited, 'true' is pushed on the IsParentAJoin stack.</span></span> <span data-ttu-id="7fed2-115">Join4 の左辺の入力である Join1 にアクセスする直前に、ビジターの状態は次の図に示すようになります。</span><span class="sxs-lookup"><span data-stu-id="7fed2-115">Right before Join1, which is the left input of Join4, is visited, the state of the visitor is as shown in the next figure.</span></span>  
  
 <span data-ttu-id="7fed2-116">![ダイアグラム](../../../../../docs/framework/data/adonet/ef/media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span><span class="sxs-lookup"><span data-stu-id="7fed2-116">![Diagram](../../../../../docs/framework/data/adonet/ef/media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span></span>  
  
 <span data-ttu-id="7fed2-117">結合のビジット メソッドが Join4 に対して呼び出されると、IsParentAJoin は true になるため、現在の SELECT ステートメントである SelectStatement0 が再利用されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-117">When the join visit method is invoked over Join4, IsParentAJoin is true, thus it reuses the current select statement SelectStatement0.</span></span> <span data-ttu-id="7fed2-118">新しいスコープ (scope1) が追加されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-118">A new scope is entered (scope1).</span></span> <span data-ttu-id="7fed2-119">左辺の子である Extent1 にアクセスする前に、もう 1 度 true が IsParentAJoin スタックにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-119">Before visiting its left child, Extent1, another true is pushed on the IsParentAJoin stack.</span></span>  
  
 <span data-ttu-id="7fed2-120">Extent1 にアクセスすると、IsParentAJoin が true を返すため、"[dbo].[Products]" を含む SqlBuilder が返されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-120">When Extent1 is visited, because IsParentAJoin returns true, it returns a SqlBuilder containing "[dbo].[Products]".</span></span> <span data-ttu-id="7fed2-121">制御が、Join4 にアクセスしているメソッドに戻されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-121">The control returns to the method visiting Join4.</span></span> <span data-ttu-id="7fed2-122">エントリが IsParentAJoin からポップされ、ProcessJoinInputResult が呼び出されます。それによって、Extent1 へのアクセス結果が SelectStatement0 の FROM 句に追加されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-122">An entry is popped from IsParentAJoin, and ProcessJoinInputResult is called, which appends the result of visiting Extent1 to the From clause of SelectStatement0.</span></span> <span data-ttu-id="7fed2-123">入力バインディング名 "Extent1" の新しい from シンボルである symbol_Extent1 が作成され、SelectStatement0 の FromExtents に追加され、さらに "As" と symbol_Extent1 が FROM 句に追加されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-123">A new from symbol, symbol_Extent1, for the input binding name "Extent1" is created, added to the FromExtents of SelectStatement0, and also "As" and  symbol_Extent1 are appended to the from clause.</span></span> <span data-ttu-id="7fed2-124">新しいエントリが "Extent1" の AllExtentNames に追加され、値が 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-124">A new entry is added to AllExtentNames for "Extent1" with the value of 0.</span></span> <span data-ttu-id="7fed2-125">新しいエントリがシンボル テーブルの現在のスコープに追加され、"Extent1" にそのシンボル symbol_Extent1 が関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-125">A new entry is added to the current scope in the symbol table to associate "Extent1" with its symbol symbol_Extent1.</span></span> <span data-ttu-id="7fed2-126">また、symbol_Extent1 は SqlSelectStatement の AllJoinExtents にも追加されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-126">Symbol_Extent1 is also added to the AllJoinExtents of the SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="7fed2-127">Join1 の右辺の入力にアクセスする前に、"LEFT OUTER JOIN" が SelectStatement0 の FROM 句に追加されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-127">Before the right input of Join1 is visited, "LEFT OUTER JOIN" is added to the From clause of SelectStatement0.</span></span> <span data-ttu-id="7fed2-128">右辺の入力はスキャン式であるため、再度 true が IsParentAJoin スタックにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-128">Because the right input is a Scan expression, true is again pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="7fed2-129">右辺の入力にアクセスする前の状態は次の図に示すとおりです。</span><span class="sxs-lookup"><span data-stu-id="7fed2-129">The state before visiting the right input as shown in the next figure.</span></span>  
  
 <span data-ttu-id="7fed2-130">![ダイアグラム](../../../../../docs/framework/data/adonet/ef/media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span><span class="sxs-lookup"><span data-stu-id="7fed2-130">![Diagram](../../../../../docs/framework/data/adonet/ef/media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span></span>  
  
 <span data-ttu-id="7fed2-131">右辺の入力は、左辺の入力と同じように処理されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-131">The right input is processed in the same way as the left input.</span></span> <span data-ttu-id="7fed2-132">右辺の入力にアクセスした後の状態を、次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="7fed2-132">The state after visiting the right input is shown in the next figure.</span></span>  
  
 <span data-ttu-id="7fed2-133">![ダイアグラム](../../../../../docs/framework/data/adonet/ef/media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span><span class="sxs-lookup"><span data-stu-id="7fed2-133">![Diagram](../../../../../docs/framework/data/adonet/ef/media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span></span>  
  
 <span data-ttu-id="7fed2-134">次に、"false" が IsParentAJoin スタックにプッシュされ、結合条件である Var(Extent1).CategoryID == Var(Extent2).CategoryID が処理されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-134">Next "false" is pushed on the IsParentAJoin stack and the join condition Var(Extent1).CategoryID == Var(Extent2).CategoryID is processed.</span></span> <span data-ttu-id="7fed2-135">Var(Extenent1) は、シンボル テーブルの検索後、<symbol_Extent1> に解決されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-135">Var(Extenent1) is resolved to <symbol_Extent1> after a look up in the symbol table.</span></span> <span data-ttu-id="7fed2-136">インスタンスが Var(Extent1) を処理した結果の単純なシンボルに解決します。CategoryID、と共に SqlBuilder \<symbol1 > です"。CategoryID"が返されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-136">Because the instance is resolved to a simple Symbol, as a result of processing Var(Extent1).CategoryID, a SqlBuilder with \<symbol1>."CategoryID" is returned.</span></span> <span data-ttu-id="7fed2-137">同様に比較の右辺が処理され、結合条件へのアクセス結果が SelectStatement1 の FROM 句に追加され、値 "false" が IsParentAJoin スタックからポップされます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-137">Similarly the other side of the comparison is processed, and the result of visiting the join condition is appended to the FROM clause of SelectStatement1 and the value "false" is popped from the IsParentAJoin stack.</span></span>  
  
 <span data-ttu-id="7fed2-138">これで Join1 の処理が完了し、スコープがシンボル テーブルからポップされます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-138">With this, Join1 has completely been processed, and a scope is popped from the symbol table.</span></span>  
  
 <span data-ttu-id="7fed2-139">制御が、Join1 の親である Join4 の処理に戻されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-139">Control returns to processing Join4, the parent of Join1.</span></span> <span data-ttu-id="7fed2-140">子では SELECT ステートメントを再利用したため、Join1 のエクステントは単一の結合シンボル <joinSymbol_Join1> に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-140">Because the child reused the Select statement, the Join1 extents are replaced with a single Join symbol <joinSymbol_Join1>.</span></span> <span data-ttu-id="7fed2-141">また、新しいエントリがシンボル テーブルに追加され、Join1 と <joinSymbol_Join1> が関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-141">Also a new entry is added to the symbol table to associate Join1 with <joinSymbol_Join1>.</span></span>  
  
 <span data-ttu-id="7fed2-142">次に処理するノードは、Join4 の 2 つ目の子である Join3 です。</span><span class="sxs-lookup"><span data-stu-id="7fed2-142">The next node to be processed is Join3, the second child of Join4.</span></span> <span data-ttu-id="7fed2-143">これは右辺の子であるため、"false" が IsParentAJoin スタックにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-143">As it is a right child, "false" is pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="7fed2-144">この時点のビジターの状態を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="7fed2-144">The state of the visitor at this point is illustrated in the next figure.</span></span>  
  
 <span data-ttu-id="7fed2-145">![ダイアグラム](../../../../../docs/framework/data/adonet/ef/media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span><span class="sxs-lookup"><span data-stu-id="7fed2-145">![Diagram](../../../../../docs/framework/data/adonet/ef/media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span></span>  
  
 <span data-ttu-id="7fed2-146">Join3 の場合、IsParentAJoin は false を返します。また、新しい SqlSelectStatement (SelectStatement1) を開始し、それをスタックにプッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7fed2-146">For Join3, IsParentAJoin returns false and needs to start a new SqlSelectStatement (SelectStatement1) and push it on the stack.</span></span> <span data-ttu-id="7fed2-147">処理は前の結合と同じように実行されます。新しいスコープがスタックにプッシュされ、子が処理されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-147">Processing continues as it did with the previous the previous joins, a new scope is pushed on the stack and the children are processed.</span></span> <span data-ttu-id="7fed2-148">左辺の子がエクステント (Extent3) で、右辺の子が結合 (Join2) です。Join2 では、新しい SqlSelectStatement (SelectStatement2) を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7fed2-148">The left child is an Extent (Extent3) and the right child is a join (Join2) which also needs to start a new SqlSelectStatement: SelectStatement2.</span></span> <span data-ttu-id="7fed2-149">Join2 の子もエクステントであり、SelectStatement2 に集約されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-149">The children on Join2 are Extents as well and are aggregated into SelectStatement2.</span></span>  
  
 <span data-ttu-id="7fed2-150">Join2 にアクセスした直後で、その後処理 (ProcessJoinInputResult) を実行する前のビジターの状態を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="7fed2-150">The state of the visitor right after Join2 is visited, but before its post-processing (ProcessJoinInputResult) is done is shown in the next figure:</span></span>  
  
 <span data-ttu-id="7fed2-151">![ダイアグラム](../../../../../docs/framework/data/adonet/ef/media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span><span class="sxs-lookup"><span data-stu-id="7fed2-151">![Diagram](../../../../../docs/framework/data/adonet/ef/media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span></span>  
  
 <span data-ttu-id="7fed2-152">SelectStatement2 は、前の図では型指定されていない状態で示されています。これは、スタックからポップされたが、まだ親によって後処理が実行されていないためです。</span><span class="sxs-lookup"><span data-stu-id="7fed2-152">In the previous figure, SelectStatement2 is shown as free floating because it was popped out of the stack, but not yet post processed by the parent.</span></span> <span data-ttu-id="7fed2-153">親の FROM の部分に追加する必要がありますが、SELECT 句がないため、完全な SQL ステートメントではありません。</span><span class="sxs-lookup"><span data-stu-id="7fed2-153">It needs to be added to the FROM part of the parent, but it is not a complete SQL statement without a SELECT clause.</span></span> <span data-ttu-id="7fed2-154">そのため、この時点では、既定の列 (入力によって生成されるすべての列) が AddDefaultColumns メソッドによって選択リストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-154">So, at this point, the default columns (all the columns produced by its inputs) are added to the select list by the method AddDefaultColumns.</span></span> <span data-ttu-id="7fed2-155">AddDefaultColumns では、FromExtents 内のシンボルを反復処理し、スコープ内に取り込まれたすべての列をシンボルごとに追加します。</span><span class="sxs-lookup"><span data-stu-id="7fed2-155">AddDefaultColumns iterates over the symbols in FromExtents and for each symbol adds all the columns brought in scope.</span></span> <span data-ttu-id="7fed2-156">単純なシンボルの場合は、シンボルの型を参照して、追加するすべてのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="7fed2-156">For a simple symbol, it looks at the symbol type to retrieve all its properties to be added.</span></span> <span data-ttu-id="7fed2-157">また、AllColumnNames ディクショナリに列名を追加します。</span><span class="sxs-lookup"><span data-stu-id="7fed2-157">It also populates the AllColumnNames dictionary with the column names.</span></span> <span data-ttu-id="7fed2-158">完成した SelectStatement2 が SelectStatement1 の FROM 句に追加されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-158">The completed SelectStatement2 is appended to the FROM clause of SelectStatement1.</span></span>  
  
 <span data-ttu-id="7fed2-159">次に、Join2 を表す新しい結合シンボルが作成され、入れ子になっている結合としてマークされ、SelectStatement1 の AllJoinExtents とシンボル テーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-159">Next, a new join symbol is created to represent Join2, it is marked as a nested join and added to the AllJoinExtents of SelectStatement1 and added to the symbol table.</span></span>  <span data-ttu-id="7fed2-160">その後で、Join3 の結合条件である Var(Extent3).OrderID =  Var(Join2).Extent4.OrderID を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7fed2-160">Now the join condition of Join3, Var(Extent3).OrderID =  Var(Join2).Extent4.OrderID, needs to be processed.</span></span> <span data-ttu-id="7fed2-161">左辺の処理は Join1 の結合条件の場合と同様です。</span><span class="sxs-lookup"><span data-stu-id="7fed2-161">Processing of the left hand side is similar to the join condition of Join1.</span></span> <span data-ttu-id="7fed2-162">ただし、右辺 "Var(Join2).Extent4.OrderID" の処理は、結合のフラット化が必要なため異なります。</span><span class="sxs-lookup"><span data-stu-id="7fed2-162">However, the processing of the right and side "Var(Join2).Extent4.OrderID" is different because join flattening is required.</span></span>  
  
 <span data-ttu-id="7fed2-163">次の図には、DbPropertyExpression である "Var(Join2).Extent4.OrderID" を処理する直前のビジターの状態を示しています。</span><span class="sxs-lookup"><span data-stu-id="7fed2-163">The next figure shows the state of the visitor right before the DbPropertyExpression "Var(Join2).Extent4.OrderID" is processed.</span></span>  
  
 <span data-ttu-id="7fed2-164">"Var(Join2).Extent4.OrderID" にアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7fed2-164">Consider how "Var(Join2).Extent4.OrderID" is visited.</span></span> <span data-ttu-id="7fed2-165">最初に、インスタンス プロパティ "Var(Join2).Extent4" にアクセスします。これ自体が 1 つの DbPropertyExpression であり、まず、そのインスタンス "Var(Join2)" にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="7fed2-165">First, the instance property "Var(Join2).Extent4" is visited, which is another DbPropertyExpression and first visits its instance "Var(Join2)".</span></span> <span data-ttu-id="7fed2-166">シンボル テーブルの最上位のスコープで、"Join2" は <joinSymbol_join2> に解決されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-166">In the top most scope in the symbol table, "Join2" resolves to <joinSymbol_join2>.</span></span> <span data-ttu-id="7fed2-167">"Var(Join2).Extent4" を処理する DbPropertyExpression のビジット メソッドでは、そのインスタンスへのアクセス時に結合シンボルが返されたこと、および結合のフラット化が必要なことが検出されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-167">In the visit method for DbPropertyExpression processing "Var(Join2).Extent4" notice that a join symbol was returned when visiting the instance and flattening is required.</span></span>  
  
 <span data-ttu-id="7fed2-168">入れ子になっている結合であるため、結合シンボルの NameToExtent ディクショナリの "Extent4" プロパティを検索し、それを <symbol_Extent4> に解決することで、新しい <SymbolPair (joinSymbol_join2>、<symbol_Extent4>) を返します。</span><span class="sxs-lookup"><span data-stu-id="7fed2-168">Since it is a nested join, we look up the property "Extent4" in the NameToExtent dictionary of the join symbol, resolve it to <symbol_Extent4> and return a new SymbolPair(<joinSymbol_join2>, <symbol_Extent4>).</span></span> <span data-ttu-id="7fed2-169">シンボル ペアは "Var(Join2).Extent4.OrderID" のインスタンスの処理から返されるため、"OrderID" プロパティはそのシンボル ペア (<symbol_Extent4>) の ColumnPart を基に解決されます。このシンボル ペアには、それが表すエクステントの列のリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7fed2-169">Since a symbol pair is returned from the processing of the instance of "Var(Join2).Extent4.OrderID",  the property "OrderID" is resolved from the ColumnPart of that symbol pair (<symbol_Extent4>), which has a list of the columns of the extent it represents.</span></span> <span data-ttu-id="7fed2-170">そのため、"Var(Join2).Extent4.OrderID" は { <joinSymbol_Join2>, ".", <symbol_OrderID>} に解決されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-170">So, "Var(Join2).Extent4.OrderID" is resolved to { <joinSymbol_Join2>, ".", <symbol_OrderID>}.</span></span>  
  
 <span data-ttu-id="7fed2-171">Join4 の結合条件は同じように処理されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-171">The join condition of Join4 is similarly processed.</span></span> <span data-ttu-id="7fed2-172">制御は最上位の Project を処理した VisitInputExpression メソッドに戻されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-172">The control returns to the VisitInputExpression method that processed the top most project.</span></span> <span data-ttu-id="7fed2-173">返された SelectStatement0 の FromExtents を確認すると、入力は結合として識別されており、元のエクステントは削除され、結合シンボルのみを含む新しいエクステントに置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="7fed2-173">Looking at the FromExtents of the returned SelectStatement0, the input is identified as a join, and removes the original extents and replaces them with a new extent with just the Join symbol.</span></span> <span data-ttu-id="7fed2-174">また、シンボル テーブルも更新されています。次に、Project の Projection 部分を処理します。</span><span class="sxs-lookup"><span data-stu-id="7fed2-174">The symbol table is also updated and next the projection part of the Project is processed.</span></span> <span data-ttu-id="7fed2-175">プロパティの解決および結合エクステントのフラット化は前に説明したとおりです。</span><span class="sxs-lookup"><span data-stu-id="7fed2-175">The resolving of the properties and the flattening of the join extents is as described earlier.</span></span>  
  
 <span data-ttu-id="7fed2-176">![ダイアグラム](../../../../../docs/framework/data/adonet/ef/media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span><span class="sxs-lookup"><span data-stu-id="7fed2-176">![Diagram](../../../../../docs/framework/data/adonet/ef/media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span></span>  
  
 <span data-ttu-id="7fed2-177">最終的に、次の SqlSelectStatement が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-177">Finally, the following SqlSelectStatement is produced:</span></span>  
  
```  
SELECT:   
  "1", " AS ", "[C1]",  
  <symbol_Extent1>, ".", "[ProductID]", " AS ", "[ProductID]",   
  <symbol_Extent1>, ".", "[ProductName]", " AS ", "[ProductName]",  
  <symbol_Extent2>, ".", "[CategoryName]", " AS ", "[CategoryName]",  
  <joinSymbol_Join3>, ".", <symbol_ShipCountry>, " AS ", "[ShipCountry]",   
  <joinSymbol_Join3>, ".", <symbol_ProductID>, " AS ", "[ProductID1]"  
FROM: "[dbo].[Products]", " AS ", <symbol_Extent1>,   
        "LEFT OUTER JOIN ""[dbo].[Categories]", " AS ", <symbol_Extent2>, " ON ", <symbol_Extent1>, ".", "[CategoryID]", " = ", <symbol_Extent2>, ".", "[CategoryID]",   
        "INNER JOIN ",   
        " (", SELECT:   
           <symbol_Extent3>, ".", "[OrderID]", " AS ", <symbol_OrderID>, ",   
              <symbol_Extent3>, ".", "[ProductID]", " AS ", <symbol_ProductID>, ...,  
         <joinSymbol_Join2>, ".", <symbol_OrderID_2>, ", ",   
           <joinSymbol_Join2>, ".", <symbol_CustomerID>, ....,    
        <joinSymbol_Join2>, ".", <symbol_OrderID_3>,   
<joinSymbol_Join2>, ".", <symbol_CustomsDescription>,   
<joinSymbol_Join2>, ".", <symbol_ExciseTax>  
FROM: "[dbo].[OrderDetails]", " AS ", <symbol_Extent3>,   
"LEFT OUTER JOIN ",   
" (", SELECT:   
<symbol_Extent4>, ".", "[OrderID]", " AS ", <symbol_OrderID_2>,   
<symbol_Extent4>, ".", "[CustomerID]", " AS ", <symbol_CustomerID>, ...  
<symbol_Extent5>, ".", "[OrderID]", " AS ", <symbol_OrderID_3>,  
<symbol_Extent5>, ".", "[CustomsDescription]", " AS ", <symbol_CustomsDescription>,  
<symbol_Extent5>, ".", "[ExciseTax]", " AS ", <symbol_ExciseTax>  
FROM: "[dbo].[Orders]", " AS ", <symbol_Extent4>,  
"LEFT OUTER JOIN ", , "[dbo].[InternationalOrders]", " AS ", <symbol_Extent5>,   
" ON ", <symbol_Extent4>, ".", "[OrderID]", " = ", , <symbol_Extent5>, ".", "[OrderID]"  
" )", " AS ", <joinSymbol_Join2>, " ON ", , , <symbol_Extent3>, ".", "[OrderID]", " = ", , <joinSymbol_Join2>, ".", <symbol_OrderID_2>  
" )", " AS ", <joinSymbol_Join3>, " ON ", , , <symbol_Extent1>, ".", "[ProductID]", " = ", , <joinSymbol_Join3>, ".", <symbol_ProductID>  
```  
  
### <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="7fed2-178">SQL 生成の 2 番目のフェーズ: 文字列コマンドの生成</span><span class="sxs-lookup"><span data-stu-id="7fed2-178">Second Phase of SQL Generation: Generating the String Command</span></span>  
 <span data-ttu-id="7fed2-179">2 番目のフェーズでは、シンボルの実際の名前を生成します。ここでは、競合を解決する必要がある "OrderID" という名前の列を表すシンボルについてのみ説明します。</span><span class="sxs-lookup"><span data-stu-id="7fed2-179">The second phase produces actual names for the symbols, and we only focus on the symbols representing columns named "OrderID", as in this case a conflict needs to be resolved.</span></span> <span data-ttu-id="7fed2-180">これらは SqlSelectStatement で強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-180">These are highlighted in the SqlSelectStatement.</span></span> <span data-ttu-id="7fed2-181">図に使用されているサフィックスは、これらが別々のインスタンスであることを強調しているだけで、新しい名前を表しているわけではありません。その理由は、この段階では、シンボルの最終的な名前 (場合によっては元の名前とは異なる) がまだ割り当てられていないためです。</span><span class="sxs-lookup"><span data-stu-id="7fed2-181">Note that the suffixes used in the figure are only to emphasize that these are different instances, not to represent any new names, as at this stage their final names (possibly different form the original names) have not been assigned yet.</span></span>  
  
 <span data-ttu-id="7fed2-182">名前を変更する必要があるシンボルとして最初に検出されるのが、<symbol_OrderID> です。</span><span class="sxs-lookup"><span data-stu-id="7fed2-182">The first symbol found that needs to be renamed is <symbol_OrderID>.</span></span> <span data-ttu-id="7fed2-183">その新しい名前として "OrderID1" が割り当てられます。1 は、"OrderID" に対して最後に使用されたサフィックスとしてマークされ、シンボルは名前を変更する必要がないものとしてマークされます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-183">Its new name is assigned as "OrderID1", 1 is marked as the last used suffix for "OrderID" and the symbol is marked as not needing renaming.</span></span> <span data-ttu-id="7fed2-184">次に、最初に使われている <symbol_OrderID_2> が検出されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-184">Next, the first usage of <symbol_OrderID_2> is found.</span></span> <span data-ttu-id="7fed2-185">これは、有効な次のサフィックスを使用するように名前が変更され ("OrderID2")、このシンボルも名前を変更する必要がないものとしてマークされます。そのため、次に使用するときに、名前の変更は行われません。</span><span class="sxs-lookup"><span data-stu-id="7fed2-185">It is renamed to use the next available suffix ("OrderID2") and again marked as not needing renaming, so that next time it is used it does not get renamed.</span></span> <span data-ttu-id="7fed2-186">この処理は、<symbol_OrderID_3> に対しても行われます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-186">This is done for <symbol_OrderID_3> too.</span></span>  
  
 <span data-ttu-id="7fed2-187">2 番目のフェーズの最後に、最終的な SQL ステートメントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7fed2-187">At the end of the second phase, the final SQL statement is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fed2-188">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fed2-188">See Also</span></span>  
 [<span data-ttu-id="7fed2-189">サンプル プロバイダーでの SQL 生成</span><span class="sxs-lookup"><span data-stu-id="7fed2-189">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
