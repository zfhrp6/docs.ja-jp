---
title: "&#39;です。ReDim &#39;右端の次元のみ変更できます。"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 752e0e54c48b3b348a477787e5e911f1b1777667
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a><span data-ttu-id="fab59-102">&#39;です。ReDim &#39;右端の次元のみ変更できます。</span><span class="sxs-lookup"><span data-stu-id="fab59-102">&#39;ReDim&#39; can only change the right-most dimension</span></span>
<span data-ttu-id="fab59-103">`ReDim` ステートメントが `Preserve` キーワードを使用して、最後のディメンションではない配列のディメンションを変更しようとしました。</span><span class="sxs-lookup"><span data-stu-id="fab59-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="fab59-104">`Preserve`を使用すると、配列の最後のディメンションについてのみ、サイズを変更できます。</span><span class="sxs-lookup"><span data-stu-id="fab59-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="fab59-105">他のすべてのディメンションに対しては、既存の配列と同じサイズを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fab59-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fab59-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="fab59-106">To correct this error</span></span>  
  
-   <span data-ttu-id="fab59-107">`Preserve` キーワードを削除します。</span><span class="sxs-lookup"><span data-stu-id="fab59-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fab59-108">参照</span><span class="sxs-lookup"><span data-stu-id="fab59-108">See Also</span></span>  
 [<span data-ttu-id="fab59-109">Visual Basic における配列</span><span class="sxs-lookup"><span data-stu-id="fab59-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="fab59-110">Visual Basic における配列の次元</span><span class="sxs-lookup"><span data-stu-id="fab59-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="fab59-111">ReDim ステートメント</span><span class="sxs-lookup"><span data-stu-id="fab59-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="fab59-112">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="fab59-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="fab59-113">保存 - 削除</span><span class="sxs-lookup"><span data-stu-id="fab59-113">Preserve - delete</span></span>](http://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
