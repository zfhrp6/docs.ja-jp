---
title: + (文字列連結)(Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 1826d1267f0ee5ad8320cf1d1ab36f87adf765a5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="d2ca3-102">+ (文字列連結) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d2ca3-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="d2ca3-103">2 つの文字列を連結します。</span><span class="sxs-lookup"><span data-stu-id="d2ca3-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2ca3-104">構文</span><span class="sxs-lookup"><span data-stu-id="d2ca3-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="d2ca3-105">引数</span><span class="sxs-lookup"><span data-stu-id="d2ca3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d2ca3-106">EDM.String データ型の任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="d2ca3-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="d2ca3-107">両方の式は、同じデータ型でなければなりません。または、一方の式をもう一方の式のデータ型に暗黙的に変換できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2ca3-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d2ca3-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="d2ca3-108">Result Types</span></span>  
 <span data-ttu-id="d2ca3-109">2 つの引数の暗黙の型の昇格の結果であるデータ型。</span><span class="sxs-lookup"><span data-stu-id="d2ca3-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="d2ca3-110">暗黙的な型の昇格の詳細については、次を参照してください。[型システム](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="d2ca3-110">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2ca3-111">例</span><span class="sxs-lookup"><span data-stu-id="d2ca3-111">Example</span></span>  
 <span data-ttu-id="d2ca3-112">次の Entity SQL クエリでは、+ 演算子を使用して、2 つの文字列を連結します。</span><span class="sxs-lookup"><span data-stu-id="d2ca3-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="d2ca3-113">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="d2ca3-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d2ca3-114">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d2ca3-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d2ca3-115">」の手順に従って[する方法: PrimitiveType 結果が返されますそのクエリを実行する](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)です。</span><span class="sxs-lookup"><span data-stu-id="d2ca3-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="d2ca3-116">次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="d2ca3-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="d2ca3-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2ca3-117">See Also</span></span>  
 [<span data-ttu-id="d2ca3-118">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="d2ca3-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="d2ca3-119">概念モデルの型 (CSDL)</span><span class="sxs-lookup"><span data-stu-id="d2ca3-119">Conceptual Model Types (CSDL)</span></span>](http://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
