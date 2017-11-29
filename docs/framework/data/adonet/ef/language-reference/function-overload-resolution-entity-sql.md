---
title: "関数のオーバーロードの解決方法 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f46bc1712946ec26f2ab1cbece7603a5336a831e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="function-overload-resolution-entity-sql"></a><span data-ttu-id="6fe64-102">関数のオーバーロードの解決方法 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6fe64-102">Function Overload Resolution (Entity SQL)</span></span>
<span data-ttu-id="6fe64-103">このトピックでは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 関数の解決方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6fe64-103">This topic describes how [!INCLUDE[esql](../../../../../../includes/esql-md.md)] functions are resolved.</span></span>  
  
 <span data-ttu-id="6fe64-104">それぞれのシグネチャが一意であれば、複数の関数を同じ名前で定義することは可能です。</span><span class="sxs-lookup"><span data-stu-id="6fe64-104">More than one function can be defined with the same name, as long as the functions have unique signatures.</span></span>  
  
 <span data-ttu-id="6fe64-105">その場合、式でどの関数が参照されているのかを判断するには、以下の基準を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6fe64-105">When this is the case, the following criteria must be applied to determine which function is referenced by a given expression.</span></span> <span data-ttu-id="6fe64-106">これらの基準は順番に適用されます。</span><span class="sxs-lookup"><span data-stu-id="6fe64-106">These criteria are applied in sequence.</span></span> <span data-ttu-id="6fe64-107">1 つの関数のみに該当する最初の基準が、どの関数に解決されるかを決定します。</span><span class="sxs-lookup"><span data-stu-id="6fe64-107">The first criterion that applies only to a single function is the resolved function.</span></span>  
  
1.  <span data-ttu-id="6fe64-108">**パラメーター番号**です。</span><span class="sxs-lookup"><span data-stu-id="6fe64-108">**Parameter number**.</span></span> <span data-ttu-id="6fe64-109">関数が、式で指定されているパラメーター数と同じ数のパラメーターを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="6fe64-109">The function has the same number of parameters specified in the expression.</span></span>  
  
2.  <span data-ttu-id="6fe64-110">**型の完全一致**です。</span><span class="sxs-lookup"><span data-stu-id="6fe64-110">**Exact match on type**.</span></span> <span data-ttu-id="6fe64-111">関数の各引数の型が、パラメーターの型と完全に一致するか、NULL リテラルになっています。</span><span class="sxs-lookup"><span data-stu-id="6fe64-111">Each argument type of the function exactly matches the parameter type, or is the null literal.</span></span>  
  
3.  <span data-ttu-id="6fe64-112">**サブタイプの一致**です。</span><span class="sxs-lookup"><span data-stu-id="6fe64-112">**Match on subtype**.</span></span> <span data-ttu-id="6fe64-113">関数の各引数の型が、パラメーターの型に完全に一致するか、そのサブタイプになっています。または、引数が NULL リテラルになっています。</span><span class="sxs-lookup"><span data-stu-id="6fe64-113">Each argument type of the function exactly matches or is a sub-type of the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="6fe64-114">複数の関数が、必要なサブタイプの型変換数においてのみ異なる場合は、最も少ないサブタイプの型変換数を持つ関数が、解決された関数になります。</span><span class="sxs-lookup"><span data-stu-id="6fe64-114">In the event that several functions differ only in the number of sub-type conversions required, the function with the least number of sub-type conversions is the resolved function.</span></span>  
  
4.  <span data-ttu-id="6fe64-115">**サブタイプまたは型の昇格との一致**です。</span><span class="sxs-lookup"><span data-stu-id="6fe64-115">**Match on subtype or type promotion**.</span></span> <span data-ttu-id="6fe64-116">関数の各引数の型が、パラメーターの型に完全に一致しているか、そのサブタイプであるか、その型に昇格できます。または、引数が NULL リテラルになっています。</span><span class="sxs-lookup"><span data-stu-id="6fe64-116">Each argument type of the function exactly matches, is a sub-type of, or can be promoted to the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="6fe64-117">ここでも、複数の関数が、サブタイプの型変換および昇格の数においてのみ異なる場合は、最も少ないサブタイプの型変換および昇格の数を持つ関数が、解決された関数になります。</span><span class="sxs-lookup"><span data-stu-id="6fe64-117">Again, in the event that several functions differ only in the number of sub-type conversions and promotions, the function with the least number of sub-type conversions and promotions is the resolved function.</span></span>  
  
 <span data-ttu-id="6fe64-118">これらの基準のいずれによっても 1 つの関数を選択できない場合、関数の呼び出し式はあいまいになります。</span><span class="sxs-lookup"><span data-stu-id="6fe64-118">If none of these criteria result in a single function being selected, the function invocation expression is ambiguous.</span></span>  
  
 <span data-ttu-id="6fe64-119">これらの規則を使用して 1 つの関数を抽出できても、引数がパラメーターに一致しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="6fe64-119">Even if a single function can be extracted using these rules, the arguments still might not match the parameters.</span></span> <span data-ttu-id="6fe64-120">この場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="6fe64-120">An error is raised in this case.</span></span>  
  
 <span data-ttu-id="6fe64-121">ユーザー定義関数の場合、そのユーザー定義関数に適したシグネチャとモデル定義関数が存在する場合でも、インライン クエリ関数の定義が優先されます。</span><span class="sxs-lookup"><span data-stu-id="6fe64-121">For user-defined functions, the definition for an inline query function takes precedence even when a model-defined function exists with a signature that is a better match for the user-defined function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fe64-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="6fe64-122">See Also</span></span>  
 [<span data-ttu-id="6fe64-123">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="6fe64-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="6fe64-124">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="6fe64-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="6fe64-125">関数</span><span class="sxs-lookup"><span data-stu-id="6fe64-125">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
