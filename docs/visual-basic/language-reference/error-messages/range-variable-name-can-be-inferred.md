---
title: "範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords: BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c986fcf188482c526c53ddf3019cec5163d0b62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="e3899-102">範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます</span><span class="sxs-lookup"><span data-stu-id="e3899-102">Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="e3899-103">1 つまたは複数の引数を受け取るプログラミング要素は、LINQ クエリに含まれます。</span><span class="sxs-lookup"><span data-stu-id="e3899-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="e3899-104">コンパイラは、このプログラミング要素の範囲変数を推論できません。</span><span class="sxs-lookup"><span data-stu-id="e3899-104">The compiler is unable to infer a range variable from that programming element.</span></span>  
  
 <span data-ttu-id="e3899-105">**エラー ID:** BC36599</span><span class="sxs-lookup"><span data-stu-id="e3899-105">**Error ID:** BC36599</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e3899-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="e3899-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="e3899-107">次のコードに示すように、プログラミング要素の明示的な変数名を指定します。</span><span class="sxs-lookup"><span data-stu-id="e3899-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3899-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3899-108">See Also</span></span>  
 [<span data-ttu-id="e3899-109">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="e3899-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="e3899-110">Select 句</span><span class="sxs-lookup"><span data-stu-id="e3899-110">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
