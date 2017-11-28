---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06770f05aabedcf13cc9af1970a2c511a30c73b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="a5b16-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5b16-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="a5b16-103">プロシージャのパラメーターが、指定した型の要素のオプション配列を受け取ることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a5b16-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="a5b16-104">`ParamArray`パラメーター リストの最後のパラメーターでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a5b16-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5b16-105">コメント</span><span class="sxs-lookup"><span data-stu-id="a5b16-105">Remarks</span></span>  
 <span data-ttu-id="a5b16-106">`ParamArray`プロシージャに任意の数の引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="a5b16-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="a5b16-107">A`ParamArray`宣言されたパラメーターを常に使用する[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)です。</span><span class="sxs-lookup"><span data-stu-id="a5b16-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="a5b16-108">1 つまたは複数の引数を指定することができます、`ParamArray`適切なデータの配列を渡すことによってパラメーターの型、値、または何ものコンマ区切りの一覧にします。</span><span class="sxs-lookup"><span data-stu-id="a5b16-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="a5b16-109">詳細についてを参照してください"の呼び出しを ParamArray"[パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)です。</span><span class="sxs-lookup"><span data-stu-id="a5b16-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a5b16-110">無制限に大きくなることが、配列を処理するたびに、アプリケーションの内部の容量を超過してしまうリスクがあります。</span><span class="sxs-lookup"><span data-stu-id="a5b16-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="a5b16-111">呼び出し元のコード、パラメーター配列を同意する場合は、その長さをテストしはアプリケーションには大きすぎる場合は、適切な手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5b16-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="a5b16-112">`ParamArray` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a5b16-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="a5b16-113">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="a5b16-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="a5b16-114">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="a5b16-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="a5b16-115">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="a5b16-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="a5b16-116">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="a5b16-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a5b16-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5b16-117">See Also</span></span>  
 [<span data-ttu-id="a5b16-118">キーワード</span><span class="sxs-lookup"><span data-stu-id="a5b16-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="a5b16-119">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="a5b16-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
