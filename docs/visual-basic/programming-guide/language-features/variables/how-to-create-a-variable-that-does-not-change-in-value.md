---
title: "方法: 値の変わらない変数を作成する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1475553e64fef92ec3f3bb7e1b4fbfb357dbec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="9fd73-102">方法: 値の変わらない変数を作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fd73-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>
<span data-ttu-id="9fd73-103">その値が変化しない変数の概念は、矛盾する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9fd73-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="9fd73-104">定数は実行可能でない場合もありますし、固定値を持つ変数を使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="9fd73-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="9fd73-105">このようなケースで付きのメンバー変数を定義することができます、 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)キーワード。</span><span class="sxs-lookup"><span data-stu-id="9fd73-105">In such a case you can define a member variable with the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
 <span data-ttu-id="9fd73-106">使用することはできません、 [Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)宣言して、次の状況に、定数値を代入します。</span><span class="sxs-lookup"><span data-stu-id="9fd73-106">You cannot use the [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>  
  
-   <span data-ttu-id="9fd73-107">`Const`ステートメントには、使用するデータ型は受け入れません。</span><span class="sxs-lookup"><span data-stu-id="9fd73-107">The `Const` statement does not accept the data type you want to use</span></span>  
  
-   <span data-ttu-id="9fd73-108">コンパイル時に値がわからない</span><span class="sxs-lookup"><span data-stu-id="9fd73-108">You do not know the value at compile time</span></span>  
  
-   <span data-ttu-id="9fd73-109">コンパイル時に定数値を計算できません。</span><span class="sxs-lookup"><span data-stu-id="9fd73-109">You are unable to compute the constant value at compile time</span></span>  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="9fd73-110">値の変わらない変数を作成するには</span><span class="sxs-lookup"><span data-stu-id="9fd73-110">To create a variable that does not change in value</span></span>  
  
1.  <span data-ttu-id="9fd73-111">モジュール レベルでのメンバー変数を宣言、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)、含めると、 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)キーワード。</span><span class="sxs-lookup"><span data-stu-id="9fd73-111">At module level, declare a member variable with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     <span data-ttu-id="9fd73-112">指定できます`ReadOnly`メンバー変数に対してのみです。</span><span class="sxs-lookup"><span data-stu-id="9fd73-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="9fd73-113">つまり、すべてのプロシージャの外部でのモジュール レベル変数を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fd73-113">This means you must define the variable at module level, outside of any procedure.</span></span>  
  
2.  <span data-ttu-id="9fd73-114">コンパイル時に単一のステートメントで値を計算する場合で初期化句を使用して、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="9fd73-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="9fd73-115">以下の[として](../../../../visual-basic/language-reference/statements/as-clause.md)等号 (=) を含む句 (`=`)、式でその後にします。</span><span class="sxs-lookup"><span data-stu-id="9fd73-115">Follow the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="9fd73-116">必ず、コンパイラは定数値には、この式を評価できます。</span><span class="sxs-lookup"><span data-stu-id="9fd73-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     <span data-ttu-id="9fd73-117">値を割り当てることができます、`ReadOnly`変数を一度だけです。</span><span class="sxs-lookup"><span data-stu-id="9fd73-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="9fd73-118">これを行うと、コードが変更できるなしの値。</span><span class="sxs-lookup"><span data-stu-id="9fd73-118">Once you do so, no code can ever change its value.</span></span>  
  
     <span data-ttu-id="9fd73-119">、コンパイル時に値がわからないか単一のステートメントでは、コンパイル時に計算できない場合は、コンス トラクターで実行時にも割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="9fd73-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="9fd73-120">これを行うには、宣言する必要があります、`ReadOnly`クラスまたは構造体のレベルで変数。</span><span class="sxs-lookup"><span data-stu-id="9fd73-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="9fd73-121">そのクラスまたは構造体のコンス トラクターで、変数の固定値を計算し、コンス トラクターから戻る前に、変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9fd73-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fd73-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fd73-122">See Also</span></span>  
 [<span data-ttu-id="9fd73-123">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="9fd73-123">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [<span data-ttu-id="9fd73-124">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="9fd73-124">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
