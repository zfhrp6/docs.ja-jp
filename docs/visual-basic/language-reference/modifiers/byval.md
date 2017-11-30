---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c192cdb4ac43ad614fbfb663079c03ddc6c358c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="byval-visual-basic"></a><span data-ttu-id="2340d-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2340d-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="2340d-103">呼び出されたプロシージャまたはプロパティが呼び出し元のコードで引数の基になる変数の値を変更できないように引数が渡されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2340d-103">Specifies that an argument is passed in such a way that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2340d-104">コメント</span><span class="sxs-lookup"><span data-stu-id="2340d-104">Remarks</span></span>  
 <span data-ttu-id="2340d-105">`ByVal` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2340d-105">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="2340d-106">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="2340d-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="2340d-107">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="2340d-107">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="2340d-108">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="2340d-108">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="2340d-109">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="2340d-109">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="2340d-110">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="2340d-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="2340d-111">例</span><span class="sxs-lookup"><span data-stu-id="2340d-111">Example</span></span>  
 <span data-ttu-id="2340d-112">次の例での使用、`ByVal`参照型の引数の渡しのパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="2340d-112">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="2340d-113">例では、引数は`c1`、クラスのインスタンス`Class1`です。</span><span class="sxs-lookup"><span data-stu-id="2340d-113">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="2340d-114">`ByVal`手順でコードの参照の引数の基になる値の変更を防止`c1`、アクセス可能なフィールドおよびのプロパティは保護されませんが、`c1`です。</span><span class="sxs-lookup"><span data-stu-id="2340d-114">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2340d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="2340d-115">See Also</span></span>  
 [<span data-ttu-id="2340d-116">キーワード</span><span class="sxs-lookup"><span data-stu-id="2340d-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="2340d-117">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="2340d-117">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
