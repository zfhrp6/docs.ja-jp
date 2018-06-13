---
title: DLL を正しく呼び出せません。
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: d8c7f7aea46162215115689305f4010cb513b020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583839"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="52057-102">DLL を正しく呼び出せません。</span><span class="sxs-lookup"><span data-stu-id="52057-102">Bad DLL calling convention</span></span>
<span data-ttu-id="52057-103">ダイナミック リンク ライブラリ (DLL) に渡された引数が、ルーチンによって予測されるを正確に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52057-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="52057-104">呼び出し規約は、サーバーの数、種類、および引数の順序を使用します。</span><span class="sxs-lookup"><span data-stu-id="52057-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="52057-105">プログラムが間違った型または引数の数が渡される DLL にルーチンを呼び出している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="52057-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="52057-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="52057-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="52057-107">すべての引数の型が呼び出しには、ルーチンの宣言で指定されている条項に同意することを確認します。</span><span class="sxs-lookup"><span data-stu-id="52057-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2.  <span data-ttu-id="52057-108">同じ数の呼び出しには、ルーチンの宣言に示されている引数を渡していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="52057-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3.  <span data-ttu-id="52057-109">DLL 内のルーチンは、値によって引数が必要ですが場合、確認`ByVal`ルーチンの宣言でこれらの引数が指定されています。</span><span class="sxs-lookup"><span data-stu-id="52057-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52057-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="52057-110">See Also</span></span>  
 [<span data-ttu-id="52057-111">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="52057-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="52057-112">Call ステートメント</span><span class="sxs-lookup"><span data-stu-id="52057-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)  
 [<span data-ttu-id="52057-113">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="52057-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
