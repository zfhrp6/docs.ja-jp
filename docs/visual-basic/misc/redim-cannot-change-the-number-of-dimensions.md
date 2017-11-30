---
title: "&#39;です。ReDim &#39;次元数を変更することはできません。"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cf3713c72bd07803935065780e894c130911a6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39redim39-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="46106-102">&#39;です。ReDim &#39;次元数を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="46106-102">&#39;ReDim&#39; cannot change the number of dimensions</span></span>
<span data-ttu-id="46106-103">`ReDim` ステートメントを使用して、配列のランク (次元の数) を変更する操作が行われました。</span><span class="sxs-lookup"><span data-stu-id="46106-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="46106-104">`ReDim` は既に宣言された配列の 1 つ以上の次元のサイズを変更するために使用できますが、配列のランクを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="46106-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="46106-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="46106-105">To correct this error</span></span>  
  
-   <span data-ttu-id="46106-106">次元のサイズではなく、配列のランクを変更しようとしていることを確認します。可能な場合は、 `Dim` を使用して、希望のランクを持つ配列を新規に宣言します。</span><span class="sxs-lookup"><span data-stu-id="46106-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46106-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="46106-107">See Also</span></span>  
 [<span data-ttu-id="46106-108">Visual Basic における配列</span><span class="sxs-lookup"><span data-stu-id="46106-108">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="46106-109">Visual Basic における配列の次元</span><span class="sxs-lookup"><span data-stu-id="46106-109">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="46106-110">ReDim ステートメント</span><span class="sxs-lookup"><span data-stu-id="46106-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="46106-111">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="46106-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
