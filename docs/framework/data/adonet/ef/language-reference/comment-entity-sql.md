---
title: -- (コメント) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 4b3c801999d520a775c1a7026c945c027145b59d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764165"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="1e1ce-102">-- (コメント) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1e1ce-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="1e1ce-103"> クエリには、コメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="1e1ce-103"> queries can contain comments.</span></span> <span data-ttu-id="1e1ce-104">コメント行の先頭には、2 個のダッシュ (`--`) を付けます。</span><span class="sxs-lookup"><span data-stu-id="1e1ce-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e1ce-105">構文</span><span class="sxs-lookup"><span data-stu-id="1e1ce-105">Syntax</span></span>  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="1e1ce-106">引数</span><span class="sxs-lookup"><span data-stu-id="1e1ce-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="1e1ce-107">コメントのテキストを表す文字列です。</span><span class="sxs-lookup"><span data-stu-id="1e1ce-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e1ce-108">例</span><span class="sxs-lookup"><span data-stu-id="1e1ce-108">Example</span></span>  
 <span data-ttu-id="1e1ce-109">次の Entity SQL クエリは、コメントの使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="1e1ce-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="1e1ce-110">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="1e1ce-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1e1ce-111">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1e1ce-111">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1e1ce-112">「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="1e1ce-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="1e1ce-113">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="1e1ce-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="1e1ce-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e1ce-114">See Also</span></span>  
 [<span data-ttu-id="1e1ce-115">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="1e1ce-115">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="1e1ce-116">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="1e1ce-116">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
