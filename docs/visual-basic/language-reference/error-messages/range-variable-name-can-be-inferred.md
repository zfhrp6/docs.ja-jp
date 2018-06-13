---
title: 範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: d6d082511d501b961b537317f0cb17bcd1c9370b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594622"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="fe73c-102">範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます</span><span class="sxs-lookup"><span data-stu-id="fe73c-102">Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="fe73c-103">1 つまたは複数の引数を受け取るプログラミング要素は、LINQ クエリに含まれます。</span><span class="sxs-lookup"><span data-stu-id="fe73c-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="fe73c-104">コンパイラは、このプログラミング要素の範囲変数を推論できません。</span><span class="sxs-lookup"><span data-stu-id="fe73c-104">The compiler is unable to infer a range variable from that programming element.</span></span>  
  
 <span data-ttu-id="fe73c-105">**エラー ID:** BC36599</span><span class="sxs-lookup"><span data-stu-id="fe73c-105">**Error ID:** BC36599</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fe73c-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="fe73c-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="fe73c-107">次のコードに示すように、プログラミング要素の明示的な変数名を指定します。</span><span class="sxs-lookup"><span data-stu-id="fe73c-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe73c-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe73c-108">See Also</span></span>  
 [<span data-ttu-id="fe73c-109">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="fe73c-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="fe73c-110">Select 句</span><span class="sxs-lookup"><span data-stu-id="fe73c-110">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
