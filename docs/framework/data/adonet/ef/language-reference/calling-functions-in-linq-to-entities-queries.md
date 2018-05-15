---
title: LINQ to Entities クエリ内の関数の呼び出し
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 690f1a2cdcd8726d40a6627c1ceb05c9ae7e7fdd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="2ebaf-102">LINQ to Entities クエリ内の関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="2ebaf-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="2ebaf-103">このセクションの各トピックでは、LINQ to Entities クエリで関数を呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ebaf-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="2ebaf-104"><xref:System.Data.Objects.EntityFunctions> クラスおよび <xref:System.Data.Objects.SqlClient.SqlFunctions> クラスを使用すると、Entity Framework の一部として正規関数およびデータベース関数にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2ebaf-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="2ebaf-105">詳細については、次を参照してください。[する方法: 正規の関数を呼び出す](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)と[する方法: データベース関数を呼び出す](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)です。</span><span class="sxs-lookup"><span data-stu-id="2ebaf-105">For more information, see [How to: Call Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) and [How to: Call Database Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="2ebaf-106">カスタム関数を呼び出すプロセスには、3 つの基本的な手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="2ebaf-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1.  <span data-ttu-id="2ebaf-107">概念モデルで関数を定義するか、ストレージ モデルで関数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="2ebaf-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2.  <span data-ttu-id="2ebaf-108">メソッドをアプリケーションに追加し、<xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> を使用してこれをモデルの関数にマップします。</span><span class="sxs-lookup"><span data-stu-id="2ebaf-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3.  <span data-ttu-id="2ebaf-109">LINQ to Entities クエリから関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2ebaf-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="2ebaf-110">詳細については、このセクションの各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ebaf-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ebaf-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2ebaf-111">In This Section</span></span>  
 [<span data-ttu-id="2ebaf-112">正規関数を呼び出す方法</span><span class="sxs-lookup"><span data-stu-id="2ebaf-112">How to: Call Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="2ebaf-113">データベース関数を呼び出す方法</span><span class="sxs-lookup"><span data-stu-id="2ebaf-113">How to: Call Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [<span data-ttu-id="2ebaf-114">カスタム データベース関数を呼び出す方法</span><span class="sxs-lookup"><span data-stu-id="2ebaf-114">How to: Call Custom Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="2ebaf-115">方法: クエリを使用してモデル定義関数を呼び出す</span><span class="sxs-lookup"><span data-stu-id="2ebaf-115">How to: Call Model-Defined Functions in Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="2ebaf-116">方法: モデル定義関数をオブジェクト メソッドとして呼び出す</span><span class="sxs-lookup"><span data-stu-id="2ebaf-116">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="2ebaf-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ebaf-117">See Also</span></span>  
 [<span data-ttu-id="2ebaf-118">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="2ebaf-118">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="2ebaf-119">正規関数</span><span class="sxs-lookup"><span data-stu-id="2ebaf-119">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)  
 [<span data-ttu-id="2ebaf-120">.edmx ファイルの概要</span><span class="sxs-lookup"><span data-stu-id="2ebaf-120">.edmx File Overview</span></span>](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="2ebaf-121">方法: カスタム関数を概念モデルの定義</span><span class="sxs-lookup"><span data-stu-id="2ebaf-121">How to: Define Custom Functions in the Conceptual Model</span></span>](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)
