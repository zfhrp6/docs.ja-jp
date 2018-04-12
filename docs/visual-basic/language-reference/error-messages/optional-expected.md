---
title: '&#39;以外の場合は省略可能な &#39;です。必要です。'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e84371935fdd2d558e6828c05fa952b9cc4cf4f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="39optional39-expected"></a><span data-ttu-id="ba516-102">&#39;以外の場合は省略可能な &#39;です。必要です。</span><span class="sxs-lookup"><span data-stu-id="ba516-102">&#39;Optional&#39; expected</span></span>
<span data-ttu-id="ba516-103">プロシージャの宣言で省略可能な引数には、必須の引数が続きます。</span><span class="sxs-lookup"><span data-stu-id="ba516-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="ba516-104">各引数は次のオプションの引数も省略可能な場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba516-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="ba516-105">**エラー ID:** BC30202</span><span class="sxs-lookup"><span data-stu-id="ba516-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ba516-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="ba516-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="ba516-107">引数が必要になるとしている場合は、引数リストの最初の省略可能な引数の前に移動します。</span><span class="sxs-lookup"><span data-stu-id="ba516-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="ba516-108">引数は省略可能としている場合を使用して、`Optional`キーワード。</span><span class="sxs-lookup"><span data-stu-id="ba516-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba516-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba516-109">See Also</span></span>  
 [<span data-ttu-id="ba516-110">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="ba516-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
