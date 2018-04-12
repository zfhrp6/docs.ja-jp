---
title: 範囲変数&lt;変数&gt;外側のブロックを以前に定義された範囲変数、またはクエリ式内で暗黙的に宣言された変数内の変数を非表示になります
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ccbac48694a13daa09f2511cf39d5dbd51cdaaf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="2c747-102">範囲変数&lt;変数&gt;外側のブロックを以前に定義された範囲変数、またはクエリ式内で暗黙的に宣言された変数内の変数を非表示になります</span><span class="sxs-lookup"><span data-stu-id="2c747-102">Range variable &lt;variable&gt; hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="2c747-103">指定された範囲変数の名前、 `Select`、 `From`、 `Aggregate`、または`Let`句が既に指定されている、クエリまたはクエリで暗黙的に宣言されている変数の名前で、範囲変数の名前に重複などのフィールド名または集計関数の名前。</span><span class="sxs-lookup"><span data-stu-id="2c747-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="2c747-104">**エラー ID:** BC36633</span><span class="sxs-lookup"><span data-stu-id="2c747-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2c747-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="2c747-105">To correct this error</span></span>  
  
-   <span data-ttu-id="2c747-106">特定のクエリ スコープ内のすべての範囲変数に一意の名前があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2c747-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="2c747-107">クエリは、入れ子になったクエリは、一意のスコープであることを確認するかっこで囲むことができます。</span><span class="sxs-lookup"><span data-stu-id="2c747-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c747-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c747-108">See Also</span></span>  
 [<span data-ttu-id="2c747-109">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="2c747-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="2c747-110">From 句</span><span class="sxs-lookup"><span data-stu-id="2c747-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="2c747-111">Let 句</span><span class="sxs-lookup"><span data-stu-id="2c747-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="2c747-112">Aggregate 句</span><span class="sxs-lookup"><span data-stu-id="2c747-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="2c747-113">Select 句</span><span class="sxs-lookup"><span data-stu-id="2c747-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
