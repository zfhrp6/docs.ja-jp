---
title: リレーションシップを介したクエリの実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: f5b2775b2f0c8e35d398d5d0666d47bf0009a9e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360466"
---
# <a name="querying-across-relationships"></a><span data-ttu-id="10206-102">リレーションシップを介したクエリの実行</span><span class="sxs-lookup"><span data-stu-id="10206-102">Querying Across Relationships</span></span>
<span data-ttu-id="10206-103">他のオブジェクトまたは他のオブジェクトのコレクションをクラス定義内で参照することは、データベース内の外部キー リレーションシップに直接対応します。</span><span class="sxs-lookup"><span data-stu-id="10206-103">References to other objects or collections of other objects in your class definitions directly correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="10206-104">クエリを実行するときにこのリレーションシップを使用するには、ドット表記を使ってリレーションシップ プロパティにアクセスし、オブジェクト間を移動します。</span><span class="sxs-lookup"><span data-stu-id="10206-104">You can use these relationships when you query by using dot notation to access the relationship properties and navigate from one object to another.</span></span> <span data-ttu-id="10206-105">これらのアクセス操作は、SQL で同等の複雑な結合または相関サブクエリとして変換されます。</span><span class="sxs-lookup"><span data-stu-id="10206-105">These access operations translate to more complex joins or correlated subqueries in the equivalent SQL.</span></span>  
  
 <span data-ttu-id="10206-106">たとえば、次のクエリでは、ロンドン在住の顧客からの注文のみが結果として得られるように注文から顧客へと移動します。</span><span class="sxs-lookup"><span data-stu-id="10206-106">For example, the following query navigates from orders to customers as a way to restrict the results to only those orders for customers located in London.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 <span data-ttu-id="10206-107">リレーションシップのプロパティが存在しない場合は、それらを記述する必要があるとして手動で*結合*次のコードのように、SQL クエリの場合と同様、します。</span><span class="sxs-lookup"><span data-stu-id="10206-107">If relationship properties did not exist you would have to write them manually as *joins*, just as you would do in a SQL query, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 <span data-ttu-id="10206-108">使用することができます、*リレーションシップ*プロパティを 1 回、このようなリレーションシップを定義します。</span><span class="sxs-lookup"><span data-stu-id="10206-108">You can use the *relationship* property to define this particular relationship one time.</span></span> <span data-ttu-id="10206-109">こうすると、使いやすいドット構文を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="10206-109">You can then use the more convenient dot syntax.</span></span> <span data-ttu-id="10206-110">しかし、それだけがリレーションシップ プロパティの利点ではありません。なぜなら、通常はドメイン固有のオブジェクト モデルは階層構造またはグラフとして定義されるからです。</span><span class="sxs-lookup"><span data-stu-id="10206-110">But relationship properties exist more importantly because domain-specific object models are typically defined as hierarchies or graphs.</span></span> <span data-ttu-id="10206-111">プログラムで使用するオブジェクトには他のオブジェクトへの参照が含まれます。</span><span class="sxs-lookup"><span data-stu-id="10206-111">The objects that you program against have references to other objects.</span></span> <span data-ttu-id="10206-112">このオブジェクト間リレーションシップがデータベースの外部キー型リレーションシップに相当するのは、単なる幸運な偶然です。</span><span class="sxs-lookup"><span data-stu-id="10206-112">It is only a happy coincidence that object-to-object relationships correspond to foreign-key-styled relationships in databases.</span></span> <span data-ttu-id="10206-113">プロパティへのアクセスは、結合を記述するための便利な方法となります。</span><span class="sxs-lookup"><span data-stu-id="10206-113">Property access then provides a convenient way to write joins.</span></span>  
  
 <span data-ttu-id="10206-114">この点では、リレーションシップ プロパティは、クエリそのものよりもクエリの結果でより重要です。</span><span class="sxs-lookup"><span data-stu-id="10206-114">With regard to this, relationship properties are more important on the results side of a query than as part of the query itself.</span></span> <span data-ttu-id="10206-115">クエリによって特定の顧客に関するデータが取得された後で、クラス定義ではその顧客の注文が存在することが示されます。</span><span class="sxs-lookup"><span data-stu-id="10206-115">After the query has retrieved data about a particular customer, the class definition indicates that customers have orders.</span></span> <span data-ttu-id="10206-116">つまり、特定の顧客の `Orders` プロパティにその顧客のすべての注文が含まれると見なすことができます。</span><span class="sxs-lookup"><span data-stu-id="10206-116">In other words, you expect the `Orders` property of a particular customer to be a collection that is populated with all the orders from that customer.</span></span> <span data-ttu-id="10206-117">実際には、これはクラスをこのように定義することにより宣言したコントラクトです。</span><span class="sxs-lookup"><span data-stu-id="10206-117">That is in fact the contract you declared by defining the classes in this manner.</span></span> <span data-ttu-id="10206-118">クエリによって注文が要求されなかった場合でも、ここに注文が含まれていると見なすことができます。</span><span class="sxs-lookup"><span data-stu-id="10206-118">You expect to see the orders there even if the query did not request orders.</span></span> <span data-ttu-id="10206-119">オブジェクト モデルに対して期待されるのは、それがデータベースがメモリ内に拡張されたものであり、関連オブジェクトがすぐに使用できる状態にある、という錯覚を維持することです。</span><span class="sxs-lookup"><span data-stu-id="10206-119">You expect your object model to maintain an illusion that it is an in-memory extension of the database with related objects immediately available.</span></span>  
  
 <span data-ttu-id="10206-120">リレーションシップが得られたので、クラスに定義されたリレーションシップ プロパティを参照してクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="10206-120">Now that you have relationships, you can write queries by referring to the relationship properties defined in your classes.</span></span> <span data-ttu-id="10206-121">これらのリレーションシップ参照は、データベース内の外部キー リレーションシップに対応します。</span><span class="sxs-lookup"><span data-stu-id="10206-121">These relationship references correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="10206-122">これらのリレーションシップを使用する操作は、SQL で同等の複雑な結合として変換されます。</span><span class="sxs-lookup"><span data-stu-id="10206-122">Operations that use these relationships translate to more complex joins in the equivalent SQL.</span></span> <span data-ttu-id="10206-123"><xref:System.Data.Linq.Mapping.AssociationAttribute> 属性を使用してリレーションシップを定義している限りは、明示的な結合を [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="10206-123">As long as you have defined a relationship (using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute), you do not have to code an explicit join in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="10206-124">この錯覚を維持するために[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]と呼ばれる手法を実装する*遅延読み込み*です。</span><span class="sxs-lookup"><span data-stu-id="10206-124">To help maintain this illusion, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implements a technique called *deferred loading*.</span></span> <span data-ttu-id="10206-125">詳細については、次を参照してください。[遅延実行と即時読み込み](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)です。</span><span class="sxs-lookup"><span data-stu-id="10206-125">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
 <span data-ttu-id="10206-126">プロジェクトの一覧を次の SQL クエリについて考えてみます`CustomerID` - `OrderID`ペア。</span><span class="sxs-lookup"><span data-stu-id="10206-126">Consider the following SQL query to project a list of `CustomerID`-`OrderID` pairs:</span></span>  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 <span data-ttu-id="10206-127">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用して同じ結果を得るには、`Orders` クラスに既に存在する `Customer` プロパティ参照を使用します。</span><span class="sxs-lookup"><span data-stu-id="10206-127">To obtain the same results by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the `Orders` property reference already existing in the `Customer` class.</span></span> <span data-ttu-id="10206-128">`Orders`リファレンスでは、クエリおよびプロジェクトの実行に必要な情報、 `CustomerID` - `OrderID`ペアは、次のコードのようにします。</span><span class="sxs-lookup"><span data-stu-id="10206-128">The `Orders` reference provides the necessary information to execute the query and project the `CustomerID`-`OrderID` pairs, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 <span data-ttu-id="10206-129">逆の操作も可能です。</span><span class="sxs-lookup"><span data-stu-id="10206-129">You can also do the reverse.</span></span> <span data-ttu-id="10206-130">つまり、`Orders` にクエリを実行し、その `Customer` リレーションシップ参照を使用して、関連付けられた `Customer` オブジェクトに関する情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="10206-130">That is, you can query `Orders` and use its `Customer` relationship reference to access information about the associated `Customer` object.</span></span> <span data-ttu-id="10206-131">次のコード プロジェクトを同じ`CustomerID` - `OrderID`ペアをクエリすることによってこの時間が、以前と同様、`Orders`の代わりに`Customers`です。</span><span class="sxs-lookup"><span data-stu-id="10206-131">The following code projects the same `CustomerID`-`OrderID` pairs as before, but this time by querying `Orders` instead of `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="10206-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="10206-132">See Also</span></span>  
 [<span data-ttu-id="10206-133">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="10206-133">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
