---
title: Erase ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 317e2a7dc5facb08388f3a3e635734e4daed5eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601794"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="c6848-102">Erase ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6848-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="c6848-103">配列変数を解放し、その要素に使用するメモリの割り当てを解除するために使用します。</span><span class="sxs-lookup"><span data-stu-id="c6848-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6848-104">構文</span><span class="sxs-lookup"><span data-stu-id="c6848-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="c6848-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="c6848-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="c6848-106">必須。</span><span class="sxs-lookup"><span data-stu-id="c6848-106">Required.</span></span> <span data-ttu-id="c6848-107">消去する配列変数の一覧です。</span><span class="sxs-lookup"><span data-stu-id="c6848-107">List of array variables to be erased.</span></span> <span data-ttu-id="c6848-108">複数の変数を指定するときは、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="c6848-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6848-109">コメント</span><span class="sxs-lookup"><span data-stu-id="c6848-109">Remarks</span></span>  
 <span data-ttu-id="c6848-110">`Erase`ステートメントはプロシージャ レベルでのみ表示できます。</span><span class="sxs-lookup"><span data-stu-id="c6848-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="c6848-111">これは、プロシージャ内でクラスまたはモジュール レベルではなくは配列を解放することを意味します。</span><span class="sxs-lookup"><span data-stu-id="c6848-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="c6848-112">`Erase`ステートメントは、割り当てることに相当`Nothing`を各配列変数にします。</span><span class="sxs-lookup"><span data-stu-id="c6848-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6848-113">例</span><span class="sxs-lookup"><span data-stu-id="c6848-113">Example</span></span>  
 <span data-ttu-id="c6848-114">次の例では、 `Erase` 2 つの配列を消去して自らのメモリを解放するステートメント (1,000 と 100 の記憶域要素では、それぞれ)。</span><span class="sxs-lookup"><span data-stu-id="c6848-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="c6848-115">`ReDim`ステートメントは、3 次元の配列に、新しい配列のインスタンスが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c6848-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c6848-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6848-116">See Also</span></span>  
 [<span data-ttu-id="c6848-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="c6848-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="c6848-118">ReDim ステートメント</span><span class="sxs-lookup"><span data-stu-id="c6848-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
