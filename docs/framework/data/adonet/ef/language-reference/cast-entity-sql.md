---
title: CAST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: b3ebd4a7fe9d9e1324210d9f4d1265115bd8617f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761442"
---
# <a name="cast-entity-sql"></a><span data-ttu-id="67c84-102">CAST (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="67c84-102">CAST (Entity SQL)</span></span>
<span data-ttu-id="67c84-103">あるデータ型の式を別のデータ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="67c84-103">Converts an expression of one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67c84-104">構文</span><span class="sxs-lookup"><span data-stu-id="67c84-104">Syntax</span></span>  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="67c84-105">引数</span><span class="sxs-lookup"><span data-stu-id="67c84-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="67c84-106">`data_type`に変換できる任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="67c84-106">Any valid expression that is convertible to `data_type`.</span></span>  
  
 `data_type`  
 <span data-ttu-id="67c84-107">対象システムで提供されるデータ型。</span><span class="sxs-lookup"><span data-stu-id="67c84-107">The target system-supplied data type.</span></span> <span data-ttu-id="67c84-108">プリミティブ (スカラー) 型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="67c84-108">It must be a primitive (scalar) type.</span></span> <span data-ttu-id="67c84-109">使用される `data_type` は、クエリのスペースによって異なります。</span><span class="sxs-lookup"><span data-stu-id="67c84-109">The `data_type` used depends on the query space.</span></span> <span data-ttu-id="67c84-110">クエリが <xref:System.Data.EntityClient.EntityCommand>で実行される場合、データ型は概念モデルで定義された型です。</span><span class="sxs-lookup"><span data-stu-id="67c84-110">If a query is executed with the <xref:System.Data.EntityClient.EntityCommand>, the data type is a type defined in the conceptual model.</span></span> <span data-ttu-id="67c84-111">詳細については、「 [CSDL Specification](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67c84-111">For more information, see [CSDL Specification](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span></span> <span data-ttu-id="67c84-112">クエリが <xref:System.Data.Objects.ObjectQuery%601>で実行される場合、データ型は共通言語ランタイム (CLR) 型です。</span><span class="sxs-lookup"><span data-stu-id="67c84-112">If a query is executed with <xref:System.Data.Objects.ObjectQuery%601>, the data type is a common language runtime (CLR) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67c84-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="67c84-113">Return Value</span></span>  
 <span data-ttu-id="67c84-114">`data_type`と同じ値が返されます。</span><span class="sxs-lookup"><span data-stu-id="67c84-114">Returns the same value as `data_type`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67c84-115">コメント</span><span class="sxs-lookup"><span data-stu-id="67c84-115">Remarks</span></span>  
 <span data-ttu-id="67c84-116">キャスト式のセマンティックスは [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] CONVERT 式と似ています。</span><span class="sxs-lookup"><span data-stu-id="67c84-116">The cast expression has similar semantics to the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] CONVERT expression.</span></span> <span data-ttu-id="67c84-117">キャスト式は、ある型の値を別の型の値に変換する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="67c84-117">The cast expression is used to convert a value of one type into a value of another type.</span></span>  
  
```  
CAST( e as T )  
```  
  
 <span data-ttu-id="67c84-118">e が S 型で、S を T に変換できる場合、上記の式は有効なキャスト式です。</span><span class="sxs-lookup"><span data-stu-id="67c84-118">If e is of some type S, and S is convertible to T, then the above expression is a valid cast expression.</span></span> <span data-ttu-id="67c84-119">T はプリミティブ (スカラー) 型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="67c84-119">T must be a primitive (scalar) type.</span></span>  
  
 <span data-ttu-id="67c84-120">`Edm.Decimal`にキャストする場合は、オプションで精度と小数点以下桁数のファセットの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="67c84-120">Values for the precision and scale facets may optionally be provided when casting to `Edm.Decimal`.</span></span> <span data-ttu-id="67c84-121">明示的に指定しない場合、精度と小数点以下桁数の既定値はそれぞれ 18 と 0 です。</span><span class="sxs-lookup"><span data-stu-id="67c84-121">If not explicitly provided, the default values for precision and scale are 18 and 0, respectively.</span></span> <span data-ttu-id="67c84-122">具体的には、 `Decimal`で次のオーバーロードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="67c84-122">Specifically, the following overloads are supported for `Decimal`:</span></span>  
  
-   `CAST( d as Edm.Decimal );`  
  
-   `CAST( d as Edm.Decimal(precision) );`  
  
-   `CAST( d as Edm.Decimal(precision, scale) );`  
  
 <span data-ttu-id="67c84-123">キャスト式の使用は明示的な変換と見なされます。</span><span class="sxs-lookup"><span data-stu-id="67c84-123">The use of a cast expression is considered an explicit conversion.</span></span> <span data-ttu-id="67c84-124">明示的な変換では、データが切り捨てられたり、精度が失われたりする場合があります。</span><span class="sxs-lookup"><span data-stu-id="67c84-124">Explicit conversions might truncate data or lose precision.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67c84-125">CAST はプリミティブ型と列挙メンバー型のみでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="67c84-125">CAST is only supported over primitive types and enumeration member types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67c84-126">例</span><span class="sxs-lookup"><span data-stu-id="67c84-126">Example</span></span>  
 <span data-ttu-id="67c84-127">次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリは CAST 演算子を使用して、あるデータ型の式を別のデータ型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="67c84-127">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the CAST operator to cast an expression of one data type to another.</span></span> <span data-ttu-id="67c84-128">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="67c84-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="67c84-129">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="67c84-129">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="67c84-130">」の手順に従って[する方法: PrimitiveType 結果が返されますそのクエリを実行する](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)です。</span><span class="sxs-lookup"><span data-stu-id="67c84-130">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="67c84-131">次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="67c84-131">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a><span data-ttu-id="67c84-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="67c84-132">See Also</span></span>  
 [<span data-ttu-id="67c84-133">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="67c84-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
