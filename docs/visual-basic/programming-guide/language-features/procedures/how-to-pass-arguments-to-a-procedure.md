---
title: "方法: プロシージャ (Visual Basic) に引数を渡す |Microsoft ドキュメント"
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
- arguments [Visual Basic], passing to procedures
- procedures, arguments
- procedures, parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures, calling
- argument passing, procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
caps.latest.revision: 14
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
ms.openlocfilehash: 1e0a8d5e798f25f22f53f56a7c01bd69e3e14463
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="b4887-102">方法: プロシージャに引数を渡す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4887-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="b4887-103">プロシージャを呼び出すときに、かっこで囲まれた引数リストを持つプロシージャ名に従います。</span><span class="sxs-lookup"><span data-stu-id="b4887-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="b4887-104">プロシージャに定義されたすべての必須パラメーターに対応する引数を指定して、オプションで、引数を指定することができます、`Optional`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="b4887-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="b4887-105">指定しない場合、`Optional`呼び出しのパラメーターは、すべての後続の引数を指定している場合、引数リスト内の場所をマークするコンマを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4887-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="b4887-106">など、対応するパラメーターと異なるに渡すには、データ型の引数にするかどうかに`Byte`に`String`、型チェック スイッチを設定することができます ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) に`Off`します。</span><span class="sxs-lookup"><span data-stu-id="b4887-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="b4887-107">場合`Option Strict`は`On`、いずれかを使用する必要があります変換または変換の明示的なキーワードを拡大します。</span><span class="sxs-lookup"><span data-stu-id="b4887-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="b4887-108">詳細については、次を参照してください。[拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)と[型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)します。</span><span class="sxs-lookup"><span data-stu-id="b4887-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="b4887-109">詳細については、次を参照してください。[プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)します。</span><span class="sxs-lookup"><span data-stu-id="b4887-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="b4887-110">プロシージャに&1; つまたは複数の引数を渡す</span><span class="sxs-lookup"><span data-stu-id="b4887-110">To pass one or more arguments to a procedure</span></span>  
  
1.  <span data-ttu-id="b4887-111">呼び出し元のステートメント、プロシージャ名にかっこに従います。</span><span class="sxs-lookup"><span data-stu-id="b4887-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2.  <span data-ttu-id="b4887-112">かっこの内側には、引数リストを配置します。</span><span class="sxs-lookup"><span data-stu-id="b4887-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="b4887-113">プロシージャに定義された各必須パラメーターの引数が含まれ、引数はコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="b4887-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3.  <span data-ttu-id="b4887-114">それぞれの引数は、対応するパラメーターの型、プロシージャに変換できるデータ型に評価される有効な式を定義することを確認します。</span><span class="sxs-lookup"><span data-stu-id="b4887-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4.  <span data-ttu-id="b4887-115">パラメーターとして定義されている場合[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)、引数リストに含めるか、この句を省略することができます。</span><span class="sxs-lookup"><span data-stu-id="b4887-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="b4887-116">句を省略した場合は、そのパラメーターに定義された既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b4887-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5.  <span data-ttu-id="b4887-117">引数を省略した場合、`Optional`パラメーターとパラメーター リストで別のパラメーター後に、省略されている引数の位置をマークするには、引数リスト内の余分なコンマにします。</span><span class="sxs-lookup"><span data-stu-id="b4887-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="b4887-118">次の例では、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>関数</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>。</span><span class="sxs-lookup"><span data-stu-id="b4887-118">The following example calls the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     <span data-ttu-id="b4887-119">[!code-vb[VbVbcnProcedures #&34;](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b4887-119">[!code-vb[VbVbcnProcedures#34](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]</span></span>  
  
     <span data-ttu-id="b4887-120">前の例では、必要な最初の引数は表示されるメッセージ文字列を提供します。</span><span class="sxs-lookup"><span data-stu-id="b4887-120">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="b4887-121">メッセージ ボックスに表示するボタンを指定する省略可能な第&2; パラメーターの引数を省略します。</span><span class="sxs-lookup"><span data-stu-id="b4887-121">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="b4887-122">呼び出しは、値を指定していないため`MsgBox`が既定値を使用`MsgBoxStyle.OKOnly`、のみが表示されますが、 **ok**  ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4887-122">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="b4887-123">引数リストで、2 つ目のコンマは省略すると&2; 番目の引数の場所をマークし、最後の文字列は省略可能な&3; 番目のパラメーターに渡される`MsgBox`、これは、タイトル バーに表示されるテキスト。</span><span class="sxs-lookup"><span data-stu-id="b4887-123">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4887-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4887-124">See Also</span></span>  
 <span data-ttu-id="b4887-125">[Sub プロシージャ](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="b4887-125">[Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="b4887-126"> [Function プロシージャ](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="b4887-126"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="b4887-127"> [プロパティ プロシージャ](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="b4887-127"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="b4887-128"> [演算子プロシージャ](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="b4887-128"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="b4887-129"> [方法: プロシージャのパラメーターを定義します。](./how-to-define-a-parameter-for-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="b4887-129"> [How to: Define a Parameter for a Procedure](./how-to-define-a-parameter-for-a-procedure.md) </span></span>  
<span data-ttu-id="b4887-130"> [値渡しと参照による引数渡し](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b4887-130"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="b4887-131"> [再帰プロシージャ](./recursive-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="b4887-131"> [Recursive Procedures](./recursive-procedures.md) </span></span>  
<span data-ttu-id="b4887-132"> [プロシージャのオーバー ロード](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="b4887-132"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="b4887-133"> [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="b4887-133"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="b4887-134"> [オブジェクト指向プログラミング](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)</span><span class="sxs-lookup"><span data-stu-id="b4887-134"> [Object-Oriented Programming](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)</span></span>
