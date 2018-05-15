---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: be8ddb7f9ba08535d12890d1c5c82a9b7b485f3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="9c386-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c386-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="9c386-103">プロシージャのパラメーターが、指定した型の要素のオプション配列を受け取ることを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c386-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="9c386-104">`ParamArray` パラメーター リストの最後のパラメーターでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c386-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c386-105">コメント</span><span class="sxs-lookup"><span data-stu-id="9c386-105">Remarks</span></span>  
 <span data-ttu-id="9c386-106">`ParamArray` プロシージャに任意の数の引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="9c386-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="9c386-107">A`ParamArray`宣言されたパラメーターを常に使用する[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)です。</span><span class="sxs-lookup"><span data-stu-id="9c386-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="9c386-108">1 つまたは複数の引数を指定することができます、`ParamArray`適切なデータの配列を渡すことによってパラメーターの型、値、または何ものコンマ区切りの一覧にします。</span><span class="sxs-lookup"><span data-stu-id="9c386-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="9c386-109">詳細についてを参照してください"の呼び出しを ParamArray"[パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)です。</span><span class="sxs-lookup"><span data-stu-id="9c386-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9c386-110">無制限に大きくなることが、配列を処理するたびに、アプリケーションの内部の容量を超過してしまうリスクがあります。</span><span class="sxs-lookup"><span data-stu-id="9c386-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="9c386-111">呼び出し元のコード、パラメーター配列を同意する場合は、その長さをテストしはアプリケーションには大きすぎる場合は、適切な手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c386-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="9c386-112">`ParamArray` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c386-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="9c386-113">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="9c386-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="9c386-114">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="9c386-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="9c386-115">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="9c386-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="9c386-116">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="9c386-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9c386-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c386-117">See Also</span></span>  
 [<span data-ttu-id="9c386-118">キーワード</span><span class="sxs-lookup"><span data-stu-id="9c386-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="9c386-119">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="9c386-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
