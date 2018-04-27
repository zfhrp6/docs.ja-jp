---
title: 入れ子になった制御構造 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f2c91bcdd741ef75417fe50b0c08bd0f9bd5ff80
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="ef175-102">入れ子になった制御構造 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef175-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="ef175-103">たとえば他のコントロール ステートメント内のコントロール ステートメントを配置することができます、`If...Then...Else`ブロック内で、`For...Next`ループします。</span><span class="sxs-lookup"><span data-stu-id="ef175-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="ef175-104">制御ステートメントの中に別のコントロール ステートメントの配置と呼ばれます*入れ子になった*です。</span><span class="sxs-lookup"><span data-stu-id="ef175-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="ef175-105">入れ子のレベル</span><span class="sxs-lookup"><span data-stu-id="ef175-105">Nesting Levels</span></span>  
 <span data-ttu-id="ef175-106">Visual Basic での制御構造は、複数のレベルに入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ef175-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="ef175-107">入れ子になった構造体を 1 つずつの本体をインデントして読みやすくするための一般的な方法であります。</span><span class="sxs-lookup"><span data-stu-id="ef175-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="ef175-108">統合開発環境 (IDE) のエディターでは、この自動的に行われます。</span><span class="sxs-lookup"><span data-stu-id="ef175-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="ef175-109">次の例では、プロシージャ`sumRows`マトリックスの行ごとの正の要素を一緒に追加します。</span><span class="sxs-lookup"><span data-stu-id="ef175-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
```  
Public Sub sumRows(ByVal a(,) As Double, ByRef r() As Double)  
    Dim i, j As Integer  
    For i = 0 To UBound(a, 1)  
        r(i) = 0  
        For j = 0 To UBound(a, 2)  
            If a(i, j) > 0 Then  
                r(i) = r(i) + a(i, j)  
            End If  
        Next j  
    Next i  
End Sub  
```  
  
 <span data-ttu-id="ef175-110">前の例で最初`Next`ステートメント終了内部`For`ループし、最後`Next`、外側のステートメントを閉じます`For`ループします。</span><span class="sxs-lookup"><span data-stu-id="ef175-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="ef175-111">同様に、入れ子になった`If`ステートメント、`End If`ステートメントを最も近い前に自動的に適用`If`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ef175-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="ef175-112">入れ子になった`Do`同様に、最も内側のループが`Loop`ステートメントの内側に一致する`Do`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ef175-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef175-113">多くの制御構造のキーワードをクリックすると、すべての構造のキーワードが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="ef175-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="ef175-114">たとえばをクリックすると`If`で、`If...Then...Else`構築のすべてのインスタンス`If`、 `Then`、 `ElseIf`、 `Else`、および`End If`構築では強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="ef175-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="ef175-115">移動する前または次の強調表示されているキーワード、ctrl キーと shift キーを押しながら下方向キーまたは ctrl キーと shift キーを押しながら上方向キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ef175-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="ef175-116">さまざまな種類の制御構造の入れ子</span><span class="sxs-lookup"><span data-stu-id="ef175-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="ef175-117">1 つの種類別の種類内での制御構造の入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ef175-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="ef175-118">次の例では、`With`ブロック、`For Each`ループし、入れ子になった`If`内部ブロック、`With`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="ef175-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
```  
For Each ctl As System.Windows.Forms.Control In Me.Controls  
    With ctl  
        .BackColor = System.Drawing.Color.Yellow  
        .ForeColor = System.Drawing.Color.Black  
        If .CanFocus Then  
            .Text = "Colors changed"  
            If Not .Focus() Then  
                ' Insert code to process failed focus.  
            End If  
        End If  
    End With  
Next ctl  
```  
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="ef175-119">重複する制御構造</span><span class="sxs-lookup"><span data-stu-id="ef175-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="ef175-120">制御構造が重複することはできません。</span><span class="sxs-lookup"><span data-stu-id="ef175-120">You cannot overlap control structures.</span></span> <span data-ttu-id="ef175-121">つまり、入れ子になった構造を完全に最も内側の次の構造内に必要です。</span><span class="sxs-lookup"><span data-stu-id="ef175-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="ef175-122">たとえば、次の配置は有効なため、`For`内側の前にループが終了した`With`ブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="ef175-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 <span data-ttu-id="ef175-123">![無効な入れ子のグラフィック ダイアグラム](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span><span class="sxs-lookup"><span data-stu-id="ef175-123">![Graphic diagram of invalid nesting](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span></span>  
<span data-ttu-id="ef175-124">無効な構造体を使用して対応の入れ子</span><span class="sxs-lookup"><span data-stu-id="ef175-124">Invalid nesting of For and With structures</span></span>  
  
 <span data-ttu-id="ef175-125">Visual Basic コンパイラでは、このような重複する制御構造を検出し、コンパイル時のエラーを通知します。</span><span class="sxs-lookup"><span data-stu-id="ef175-125">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef175-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef175-126">See Also</span></span>  
 [<span data-ttu-id="ef175-127">制御フロー</span><span class="sxs-lookup"><span data-stu-id="ef175-127">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="ef175-128">条件判断構造</span><span class="sxs-lookup"><span data-stu-id="ef175-128">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="ef175-129">ループ構造</span><span class="sxs-lookup"><span data-stu-id="ef175-129">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="ef175-130">その他の制御構造</span><span class="sxs-lookup"><span data-stu-id="ef175-130">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
