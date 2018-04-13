---
title: ないオーバー ロードされた &#39;&lt;methodname&gt;&#39; 縮小変換しないで、これらの引数で呼び出すことができます
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAmbiguousMatch_NarrowingConversion1
ms.assetid: 2fdbadb9-8ef1-404a-a2ed-ce5f5e55cfcb
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 636dbb082323718d8df0371751828e547d99c760
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="no-accessible-overloaded-39ltmethodnamegt39-can-be-called-with-these-arguments-without-a-narrowing-conversion"></a><span data-ttu-id="c7be0-102">ないオーバー ロードされた &#39;&lt;methodname&gt;&#39; 縮小変換しないで、これらの引数で呼び出すことができます</span><span class="sxs-lookup"><span data-stu-id="c7be0-102">No accessible overloaded &#39;&lt;methodname&gt;&#39; can be called with these arguments without a narrowing conversion</span></span>
<span data-ttu-id="c7be0-103">オーバーロードされたメソッドが呼び出されましたが、縮小変換せずに指定された引数のリストと一致するメソッドはありませんでした。</span><span class="sxs-lookup"><span data-stu-id="c7be0-103">An overloaded method was called, but no method was matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c7be0-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c7be0-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="c7be0-105">`Option Strict Off`を指定します。</span><span class="sxs-lookup"><span data-stu-id="c7be0-105">Specify `Option Strict Off`.</span></span>  
  
2.  <span data-ttu-id="c7be0-106">オーバーロードされたメソッドのシグネチャのいずれかと一致するように、引数を変更します。</span><span class="sxs-lookup"><span data-stu-id="c7be0-106">Change the arguments to match one of the signatures of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7be0-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7be0-107">See Also</span></span>  
 [<span data-ttu-id="c7be0-108">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="c7be0-108">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="c7be0-109">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="c7be0-109">Widening and Narrowing Conversions</span></span>](../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
