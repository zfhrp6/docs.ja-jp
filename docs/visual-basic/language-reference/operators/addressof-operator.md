---
title: AddressOf 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 7c229c32a3b295b4dbfe50ca2abc60d4ad5f2145
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597788"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="10b24-102">AddressOf 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10b24-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="10b24-103">特定のプロシージャを参照するプロシージャ デリゲート インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="10b24-103">Creates a procedure delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10b24-104">構文</span><span class="sxs-lookup"><span data-stu-id="10b24-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="10b24-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="10b24-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="10b24-106">必須。</span><span class="sxs-lookup"><span data-stu-id="10b24-106">Required.</span></span> <span data-ttu-id="10b24-107">新しく作成されたプロシージャ デリゲートで参照するプロシージャを指定します。</span><span class="sxs-lookup"><span data-stu-id="10b24-107">Specifies the procedure to be referenced by the newly created procedure delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10b24-108">コメント</span><span class="sxs-lookup"><span data-stu-id="10b24-108">Remarks</span></span>  
 <span data-ttu-id="10b24-109">`AddressOf`演算子で指定された関数を指して関数デリゲートを作成する`procedurename`です。</span><span class="sxs-lookup"><span data-stu-id="10b24-109">The `AddressOf` operator creates a function delegate that points to the function specified by `procedurename`.</span></span> <span data-ttu-id="10b24-110">指定したプロシージャが場合、関数デリゲートのインスタンス メソッドが、インスタンスとメソッドの両方を参照します。</span><span class="sxs-lookup"><span data-stu-id="10b24-110">When the specified procedure is an instance method then the function delegate refers to both the instance and the method.</span></span> <span data-ttu-id="10b24-111">次に、関数デリゲートが呼び出されたときに、指定したインスタンスの指定したメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="10b24-111">Then, when the function delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="10b24-112">`AddressOf`演算子は、デリゲート コンス トラクターのオペランドとして使用できますか、コンパイラによってデリゲートの型を決定できるコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="10b24-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10b24-113">例</span><span class="sxs-lookup"><span data-stu-id="10b24-113">Example</span></span>  
 <span data-ttu-id="10b24-114">この例では、`AddressOf`を処理するデリゲートを指定する演算子、`Click`ボタンのイベントです。</span><span class="sxs-lookup"><span data-stu-id="10b24-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="10b24-115">例</span><span class="sxs-lookup"><span data-stu-id="10b24-115">Example</span></span>  
 <span data-ttu-id="10b24-116">次の例では、`AddressOf`スレッドのスタートアップ関数を指定する演算子です。</span><span class="sxs-lookup"><span data-stu-id="10b24-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="10b24-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="10b24-117">See Also</span></span>  
 [<span data-ttu-id="10b24-118">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="10b24-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="10b24-119">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="10b24-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="10b24-120">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="10b24-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="10b24-121">デリゲート</span><span class="sxs-lookup"><span data-stu-id="10b24-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
