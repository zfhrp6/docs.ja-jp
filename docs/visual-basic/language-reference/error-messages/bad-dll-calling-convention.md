---
title: DLL を正しく呼び出せません。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa84e82d2fbe1041af56fdd5cc3855efd814ddf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="4d083-102">DLL を正しく呼び出せません。</span><span class="sxs-lookup"><span data-stu-id="4d083-102">Bad DLL calling convention</span></span>
<span data-ttu-id="4d083-103">ダイナミック リンク ライブラリ (DLL) に渡された引数が、ルーチンによって予測されるを正確に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d083-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="4d083-104">呼び出し規約は、サーバーの数、種類、および引数の順序を使用します。</span><span class="sxs-lookup"><span data-stu-id="4d083-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="4d083-105">プログラムが間違った型または引数の数が渡される DLL にルーチンを呼び出している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4d083-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4d083-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4d083-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="4d083-107">すべての引数の型が呼び出しには、ルーチンの宣言で指定されている条項に同意することを確認します。</span><span class="sxs-lookup"><span data-stu-id="4d083-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2.  <span data-ttu-id="4d083-108">同じ数の呼び出しには、ルーチンの宣言に示されている引数を渡していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4d083-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3.  <span data-ttu-id="4d083-109">DLL 内のルーチンは、値によって引数が必要ですが場合、確認`ByVal`ルーチンの宣言でこれらの引数が指定されています。</span><span class="sxs-lookup"><span data-stu-id="4d083-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d083-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d083-110">See Also</span></span>  
 [<span data-ttu-id="4d083-111">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="4d083-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="4d083-112">Call ステートメント</span><span class="sxs-lookup"><span data-stu-id="4d083-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)  
 [<span data-ttu-id="4d083-113">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="4d083-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
