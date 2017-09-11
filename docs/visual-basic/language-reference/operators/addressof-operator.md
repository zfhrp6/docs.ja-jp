---
title: "AddressOf 演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
dev_langs:
- VB
helpviewer_keywords:
- AddressOf operator
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: e29b7ae2a6f6040cfc8c6e0cd0c9eb055a6694e9
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="4cc16-102">AddressOf 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cc16-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="4cc16-103">特定の手順を参照するプロシージャ デリゲート インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4cc16-103">Creates a procedure delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cc16-104">構文</span><span class="sxs-lookup"><span data-stu-id="4cc16-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="4cc16-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="4cc16-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="4cc16-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="4cc16-106">Required.</span></span> <span data-ttu-id="4cc16-107">新しく作成されたプロシージャ デリゲートによって参照されるプロシージャを指定します。</span><span class="sxs-lookup"><span data-stu-id="4cc16-107">Specifies the procedure to be referenced by the newly created procedure delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cc16-108">コメント</span><span class="sxs-lookup"><span data-stu-id="4cc16-108">Remarks</span></span>  
 <span data-ttu-id="4cc16-109">`AddressOf`演算子で指定された関数を指す関数デリゲートを作成する`procedurename`です。</span><span class="sxs-lookup"><span data-stu-id="4cc16-109">The `AddressOf` operator creates a function delegate that points to the function specified by `procedurename`.</span></span> <span data-ttu-id="4cc16-110">ときに、指定したプロシージャは、インスタンス メソッド、関数デリゲートがインスタンスとメソッドの両方を指してです。</span><span class="sxs-lookup"><span data-stu-id="4cc16-110">When the specified procedure is an instance method then the function delegate refers to both the instance and the method.</span></span> <span data-ttu-id="4cc16-111">次に、関数デリゲートが呼び出されたときに、指定したインスタンスの指定したメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4cc16-111">Then, when the function delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="4cc16-112">`AddressOf`デリゲート コンス トラクターのオペランドと演算子を使用できますか、コンパイラによって、デリゲートの型を決定するコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="4cc16-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cc16-113">例</span><span class="sxs-lookup"><span data-stu-id="4cc16-113">Example</span></span>  
 <span data-ttu-id="4cc16-114">この例では、`AddressOf`を処理するデリゲートを指定する演算子、`Click`ボタンのイベントです。</span><span class="sxs-lookup"><span data-stu-id="4cc16-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 <span data-ttu-id="4cc16-115">[!code-vb[VbVbalrDelegates&#8;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4cc16-115">[!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cc16-116">例</span><span class="sxs-lookup"><span data-stu-id="4cc16-116">Example</span></span>  
 <span data-ttu-id="4cc16-117">次の例では、`AddressOf`スレッドのスタートアップ関数を指定する演算子です。</span><span class="sxs-lookup"><span data-stu-id="4cc16-117">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 <span data-ttu-id="4cc16-118">[!code-vb[VbVbalrDelegates&#9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="4cc16-118">[!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cc16-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4cc16-119">See Also</span></span>  
 <span data-ttu-id="4cc16-120">[Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4cc16-120">[Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) </span></span>  
<span data-ttu-id="4cc16-121"> [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4cc16-121"> [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="4cc16-122"> [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4cc16-122"> [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="4cc16-123"> [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)</span><span class="sxs-lookup"><span data-stu-id="4cc16-123"> [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md)</span></span>

