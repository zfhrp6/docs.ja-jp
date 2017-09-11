---
title: "コード (Visual Basic) 内の特殊文字 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
dev_langs:
- VB
helpviewer_keywords:
- special characters, in code
- parentheses, using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator
- concatenation operators, special characters in code
- concatenation operators, vs. addition operator
- '! operator'
- separators, using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator
- addition operator
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
caps.latest.revision: 21
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
ms.openlocfilehash: cd7fbce5c382c3acd88a12277a3d7899b823d049
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="e8ffd-102">コード内の特殊文字 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8ffd-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="e8ffd-103">場合がありますコードでは、アルファベットまたは数字ではない文字が特殊文字を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="e8ffd-104">句読点と特殊文字に、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]文字セットに、コンパイラやコンパイル済みプログラムを実行するタスクの定義をプログラム テキストの整理から、さまざまな用途があります。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-104">The punctuation and special characters in the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="e8ffd-105">実行するオペレーションを指定するのには使用されません。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="e8ffd-106">かっこ</span><span class="sxs-lookup"><span data-stu-id="e8ffd-106">Parentheses</span></span>  
 <span data-ttu-id="e8ffd-107">など、プロシージャを定義するときに、かっこを使用して、`Sub`または`Function`です。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="e8ffd-108">すべてのプロシージャの引数リストをかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="e8ffd-109">複雑な式で演算子の優先順位の既定の順序を上書きするには、特に変数または引数を論理グループに配置することのかっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="e8ffd-110">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-110">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="e8ffd-111">[!code-vb[VbVbcnConventions&#11;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e8ffd-111">[!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]</span></span>  
  
 <span data-ttu-id="e8ffd-112">次のコードでは、値の実行`d`8.225 との値は、`e`は 3 です。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-112">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="e8ffd-113">計算`d`の既定の優先順位を使用して`/`経由で`+`と同じ`d = b + (c / a)`します。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-113">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="e8ffd-114">計算にかっこ`e`既定の優先順位をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-114">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="e8ffd-115">[区切り記号]</span><span class="sxs-lookup"><span data-stu-id="e8ffd-115">Separators</span></span>  
 <span data-ttu-id="e8ffd-116">区切り記号は、その名前が示す: コードのセクションを区切ります。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-116">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="e8ffd-117">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、区切り記号はコロン (`:`)。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-117">In [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], the separator character is the colon (`:`).</span></span> <span data-ttu-id="e8ffd-118">別々 の行ではなく単一の行で複数のステートメントを追加する場合は、区切り記号を使用します。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-118">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="e8ffd-119">領域を節約し、コードの読みやすさが向上します。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-119">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="e8ffd-120">次の例は、コロンで区切られた&3; つのステートメントを示しています。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-120">The following example shows three statements separated by colons.</span></span>  
  
 <span data-ttu-id="e8ffd-121">[!code-vb[VbVbcnConventions&#12;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e8ffd-121">[!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]</span></span>  
  
 <span data-ttu-id="e8ffd-122">詳細については、次を参照してください。[方法: 区切りとコード内でステートメントを組み合わせて](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)します。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-122">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="e8ffd-123">コロン (`:`) 文字は、ステートメント ラベルを識別するためにも使用します。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-123">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="e8ffd-124">詳細については、次を参照してください。[方法: ラベル ステートメント](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)します。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-124">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="e8ffd-125">連結</span><span class="sxs-lookup"><span data-stu-id="e8ffd-125">Concatenation</span></span>  
 <span data-ttu-id="e8ffd-126">使用して、`&`の演算子*連結*、または文字列を一緒にリンクします。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-126">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="e8ffd-127">混同しないでください、`+`演算子で、数値を加算します。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-127">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="e8ffd-128">使用する場合、`+`数値を操作するときに連結する演算子を正しくない結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-128">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="e8ffd-129">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-129">The following example demonstrates this.</span></span>  
  
 <span data-ttu-id="e8ffd-130">[!code-vb[VbVbcnConventions&#13;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="e8ffd-130">[!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]</span></span>  
  
 <span data-ttu-id="e8ffd-131">次のコードでは、値の実行`resultA`21.01 との値は、`resultB`は「10.0111」です。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-131">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="e8ffd-132">メンバー アクセス演算子</span><span class="sxs-lookup"><span data-stu-id="e8ffd-132">Member Access Operators</span></span>  
 <span data-ttu-id="e8ffd-133">型のメンバーにアクセスするには、ドットを使用 (`.`) または感嘆符 (`!`) 型名およびメンバー名の間の演算子です。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-133">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="e8ffd-134">ドット (.)演算子</span><span class="sxs-lookup"><span data-stu-id="e8ffd-134">Dot (.) Operator</span></span>  
 <span data-ttu-id="e8ffd-135">使用して、`.`クラス、構造体、インターフェイス、または列挙体のメンバー アクセス演算子としての演算子です。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-135">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="e8ffd-136">メンバーは、フィールド、プロパティ、イベント、またはメソッドにできます。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-136">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="e8ffd-137">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-137">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="e8ffd-138">[!code-vb[VbVbcnConventions&#14;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="e8ffd-138">[!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]</span></span>  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="e8ffd-139">感嘆符 (!)演算子</span><span class="sxs-lookup"><span data-stu-id="e8ffd-139">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="e8ffd-140">使用して、`!`ディクショナリ アクセス演算子としてクラスまたはインターフェイスでのみ演算子。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-140">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="e8ffd-141">クラスまたはインターフェイスが既定のプロパティを&1; つを受け付ける必要`String`引数。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-141">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="e8ffd-142">直後の識別子、`!`演算子が文字列として既定のプロパティに渡される引数の値になります。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-142">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="e8ffd-143">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-143">The following example demonstrates this.</span></span>  
  
 <span data-ttu-id="e8ffd-144">[!code-vb[VbVbcnConventions&#15;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="e8ffd-144">[!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]</span></span>  
  
 <span data-ttu-id="e8ffd-145">3 つの出力行の`MsgBox`値を表示すべて`32856`です。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-145">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="e8ffd-146">最初の行がプロパティには、従来のアクセスを使用して`index`、もう&1; つという事実を利用する`index`クラスの既定のプロパティは、`hasDefault`クラスへのアクセスのディクショナリを使用しています。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-146">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="e8ffd-147">なおの&2; 番目のオペランド、`!`演算子は二重引用符で囲まれていない、有効な Visual Basic 識別子である必要があります (`" "`)。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-147">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="e8ffd-148">つまり、リテラル文字列または文字列変数を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-148">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="e8ffd-149">次の行を変更し、最後、`MsgBox`ために、呼び出しがエラーを生成`"X"`囲まれた文字列リテラルでは。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-149">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  <span data-ttu-id="e8ffd-150">既定のコレクションへの参照を明示的にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-150">References to default collections must be explicit.</span></span> <span data-ttu-id="e8ffd-151">具体的には、使用することはできません、`!`演算子を遅延バインディングされた変数にします。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-151">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="e8ffd-152">`!`としても使用される文字、`Single`文字を入力します。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-152">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ffd-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8ffd-153">See Also</span></span>  
 <span data-ttu-id="e8ffd-154">[プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="e8ffd-154">[Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="e8ffd-155"> [型文字](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span><span class="sxs-lookup"><span data-stu-id="e8ffd-155"> [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span></span>
