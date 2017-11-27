---
title: "名前付きの型コンストラクター (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 72a19094beb03982448a102a4c7362a026d9e611
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="d2df7-102">名前付きの型コンストラクター (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d2df7-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="d2df7-103">エンティティ型や複合型など、概念モデル標準型のインスタンスの作成に使用します。</span><span class="sxs-lookup"><span data-stu-id="d2df7-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2df7-104">構文</span><span class="sxs-lookup"><span data-stu-id="d2df7-104">Syntax</span></span>  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="d2df7-105">引数</span><span class="sxs-lookup"><span data-stu-id="d2df7-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="d2df7-106">単純な識別子および引用符で囲まれた識別子の値。</span><span class="sxs-lookup"><span data-stu-id="d2df7-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="d2df7-107">詳細については、「[識別子](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="d2df7-107">For more information see, [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="d2df7-108">型の宣言に表示される順序と同じ順序であると見なされる型の属性。</span><span class="sxs-lookup"><span data-stu-id="d2df7-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2df7-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="d2df7-109">Return Value</span></span>  
 <span data-ttu-id="d2df7-110">名前付きの複合型とエンティティ型のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="d2df7-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2df7-111">コメント</span><span class="sxs-lookup"><span data-stu-id="d2df7-111">Remarks</span></span>  
 <span data-ttu-id="d2df7-112">次の例は、標準型と複合型を作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d2df7-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="d2df7-113">次の式は、 `Person` 型のインスタンスを作成する式です。</span><span class="sxs-lookup"><span data-stu-id="d2df7-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="d2df7-114">次の式は、複合型のインスタンスを作成する式です。</span><span class="sxs-lookup"><span data-stu-id="d2df7-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="d2df7-115">次の式は、入れ子になった複合型のインスタンスを作成する式です。</span><span class="sxs-lookup"><span data-stu-id="d2df7-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="d2df7-116">次の式は、入れ子になった複合型を持つエンティティのインスタンスを作成する式です。</span><span class="sxs-lookup"><span data-stu-id="d2df7-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="d2df7-117">次の例は、複合型のプロパティを null に初期化する方法を示しています。`MyModel.ZipCode(‘98118’, null)`</span><span class="sxs-lookup"><span data-stu-id="d2df7-117">The following example shows how to initialize a property of a complex type to null:`MyModel.ZipCode(‘98118’, null)`</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2df7-118">例</span><span class="sxs-lookup"><span data-stu-id="d2df7-118">Example</span></span>  
 <span data-ttu-id="d2df7-119">次の Entity SQL クエリでは、名前付きの型コンストラクターを使用して、概念モデル型のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d2df7-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="d2df7-120">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="d2df7-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d2df7-121">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d2df7-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d2df7-122">「 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d2df7-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="d2df7-123">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="d2df7-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="d2df7-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2df7-124">See Also</span></span>  
 [<span data-ttu-id="d2df7-125">コンス トラクター</span><span class="sxs-lookup"><span data-stu-id="d2df7-125">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [<span data-ttu-id="d2df7-126">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="d2df7-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
