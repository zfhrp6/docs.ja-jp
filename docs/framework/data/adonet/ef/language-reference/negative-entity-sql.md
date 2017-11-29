---
title: "- (負)(Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0cc2ca457fe8666bddd6f4ab40d2823d9d44c591
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="4b40d-102">- (負符号) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4b40d-102">- (Negative) (Entity SQL)</span></span>
<span data-ttu-id="4b40d-103">数値式の負の値を返します。</span><span class="sxs-lookup"><span data-stu-id="4b40d-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b40d-104">構文</span><span class="sxs-lookup"><span data-stu-id="4b40d-104">Syntax</span></span>  
  
```  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b40d-105">引数</span><span class="sxs-lookup"><span data-stu-id="4b40d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4b40d-106">任意の数値データ型の有効な式。</span><span class="sxs-lookup"><span data-stu-id="4b40d-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="4b40d-107">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="4b40d-107">Result Types</span></span>  
 <span data-ttu-id="4b40d-108">`expression`のデータ型。</span><span class="sxs-lookup"><span data-stu-id="4b40d-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b40d-109">コメント</span><span class="sxs-lookup"><span data-stu-id="4b40d-109">Remarks</span></span>  
 <span data-ttu-id="4b40d-110">符号なしの型を `expression` に指定した場合、戻り値の型は、 `expression`の型と最も関連性の高い符号付きの型になります。</span><span class="sxs-lookup"><span data-stu-id="4b40d-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="4b40d-111">たとえば、 `expression` に Byte 型を指定した場合、Int16 型の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="4b40d-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b40d-112">例</span><span class="sxs-lookup"><span data-stu-id="4b40d-112">Example</span></span>  
 <span data-ttu-id="4b40d-113">次の Entity SQL クエリでは、- 算術演算子を使用して、数値式の負の値を返します。</span><span class="sxs-lookup"><span data-stu-id="4b40d-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="4b40d-114">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="4b40d-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4b40d-115">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="4b40d-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4b40d-116">「 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4b40d-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="4b40d-117">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="4b40d-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="4b40d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b40d-118">See Also</span></span>  
 [<span data-ttu-id="4b40d-119">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="4b40d-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
