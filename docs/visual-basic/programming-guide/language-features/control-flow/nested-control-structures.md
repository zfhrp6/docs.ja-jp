---
title: "制御構造 (Visual Basic) を入れ子になった |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, control flow
- control structures, nested
- conditional statements, nested
- statements [Visual Basic], control flow
- control flow, nested control statements
- structures, nested control
- nested control statements
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
caps.latest.revision: 20
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8275a0628c8593d9e6c55ef27adcde2acec31547
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="c6a22-102">入れ子になった制御構造 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6a22-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="c6a22-103">次に例を他のコントロール ステートメント内の制御ステートメントを配置することができます、`If...Then...Else`ブロック内で、`For...Next`ループします。</span><span class="sxs-lookup"><span data-stu-id="c6a22-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="c6a22-104">制御ステートメントの中に別のコントロール ステートメントの配置はモード*入れ子になった*します。</span><span class="sxs-lookup"><span data-stu-id="c6a22-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="c6a22-105">入れ子のレベル</span><span class="sxs-lookup"><span data-stu-id="c6a22-105">Nesting Levels</span></span>  
 <span data-ttu-id="c6a22-106">制御構造の[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]複数のレベルに入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="c6a22-106">Control structures in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] can be nested to as many levels as you want.</span></span> <span data-ttu-id="c6a22-107">入れ子になった構造体を&1; つずつの本体をインデントして読みやすくするための一般的な方法です。</span><span class="sxs-lookup"><span data-stu-id="c6a22-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="c6a22-108">統合開発環境 (IDE) のエディターに自動的に行われます。</span><span class="sxs-lookup"><span data-stu-id="c6a22-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="c6a22-109">次の例では、プロシージャ`sumRows`マトリックスの行ごとの正の要素を一緒に追加します。</span><span class="sxs-lookup"><span data-stu-id="c6a22-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="c6a22-110">前の例で最初の`Next`文は、内部を閉じます`For`ループし、最後`Next`ステートメントによって、外部クローズ`For`ループします。</span><span class="sxs-lookup"><span data-stu-id="c6a22-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="c6a22-111">同様に、入れ子になった`If`、ステートメント、`End If`ステートメントは、最も近い前に自動的に適用`If`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="c6a22-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="c6a22-112">入れ子になった`Do`で同様に、最も内側のループが`Loop`最も内側に一致するステートメント`Do`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="c6a22-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6a22-113">多くの制御構造のキーワードをクリックすると、すべての構造のキーワードが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6a22-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="c6a22-114">クリックすると、`If`で、`If...Then...Else`構築のすべてのインスタンス`If`、 `Then`、 `ElseIf`、 `Else`、および`End If`構造で強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6a22-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="c6a22-115">前または次の強調表示されているキーワードに移動するには、ctrl キーと shift キーを押しながら下方向キーまたは ctrl キーと shift キーを押しながら上方向をキーを押します。</span><span class="sxs-lookup"><span data-stu-id="c6a22-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="c6a22-116">さまざまな種類の制御構造の入れ子</span><span class="sxs-lookup"><span data-stu-id="c6a22-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="c6a22-117">1 つの種類の他の種類内の制御構造の入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="c6a22-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="c6a22-118">次の例では、`With`ブロック内、`For Each`ループを入れ子になった`If`の内部ブロック、`With`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="c6a22-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="c6a22-119">重複する制御構造</span><span class="sxs-lookup"><span data-stu-id="c6a22-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="c6a22-120">制御構造を重ねることはできません。</span><span class="sxs-lookup"><span data-stu-id="c6a22-120">You cannot overlap control structures.</span></span> <span data-ttu-id="c6a22-121">つまり、入れ子になった構造を完全に次の最も内側の構造内に必要です。</span><span class="sxs-lookup"><span data-stu-id="c6a22-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="c6a22-122">たとえば、次の配置は有効なため、`For`内側の前にループが終了した`With`ブロックが終了します。</span><span class="sxs-lookup"><span data-stu-id="c6a22-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 <span data-ttu-id="c6a22-123">![無効な入れ子のグラフィック ダイアグラム](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span><span class="sxs-lookup"><span data-stu-id="c6a22-123">![Graphic diagram of invalid nesting](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span></span>  
<span data-ttu-id="c6a22-124">構造体を使用して無効な入れ子</span><span class="sxs-lookup"><span data-stu-id="c6a22-124">Invalid nesting of For and With structures</span></span>  
  
 <span data-ttu-id="c6a22-125">[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラはこのような重複する制御構造体し、コンパイル時エラーが通知を検出します。</span><span class="sxs-lookup"><span data-stu-id="c6a22-125">The [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6a22-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6a22-126">See Also</span></span>  
 <span data-ttu-id="c6a22-127">[制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span><span class="sxs-lookup"><span data-stu-id="c6a22-127">[Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span></span>  
<span data-ttu-id="c6a22-128"> [条件判断構造](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span><span class="sxs-lookup"><span data-stu-id="c6a22-128"> [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span></span>  
<span data-ttu-id="c6a22-129"> [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span><span class="sxs-lookup"><span data-stu-id="c6a22-129"> [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span></span>  
<span data-ttu-id="c6a22-130"> [その他の制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)</span><span class="sxs-lookup"><span data-stu-id="c6a22-130"> [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)</span></span>
