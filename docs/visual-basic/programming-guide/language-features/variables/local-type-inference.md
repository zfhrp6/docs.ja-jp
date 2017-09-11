---
title: "ローカル型推論 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- local type inference
- vb.TypeInfer
dev_langs:
- VB
helpviewer_keywords:
- Option Infer statement
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
caps.latest.revision: 43
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
ms.openlocfilehash: af8de63eb00db917771600f0fca8f200ec451afe
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="bfa22-102">ローカル型の推論 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfa22-102">Local Type Inference (Visual Basic)</span></span>
<span data-ttu-id="bfa22-103">Visual Basic コンパイラを使用して*型の推論*なしで宣言されたローカル変数のデータ型を決定する、`As`句。</span><span class="sxs-lookup"><span data-stu-id="bfa22-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="bfa22-104">コンパイラは、初期化式の型から変数の型を推論します。</span><span class="sxs-lookup"><span data-stu-id="bfa22-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="bfa22-105">これにより、次の例のように、型を明示的に指定せず変数を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="bfa22-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="bfa22-106">宣言の結果、両方とも`num1`と`num2`整数として厳密に型指定します。</span><span class="sxs-lookup"><span data-stu-id="bfa22-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 <span data-ttu-id="bfa22-107">[!code-vb[VbVbalrTypeInference&#1;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="bfa22-107">[!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfa22-108">たくない場合`num2`として入力するのには、前の例で、`Integer`のような宣言を使用して別の種類を指定することができます`Dim num3 As Object = 3`または`Dim num4 As Double = 3`です。</span><span class="sxs-lookup"><span data-stu-id="bfa22-108">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>  
  
 <span data-ttu-id="bfa22-109">プロシージャ レベルでローカル型推論が適用されます。</span><span class="sxs-lookup"><span data-stu-id="bfa22-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="bfa22-110">(クラス、構造体、モジュール、またはインターフェイス内では、プロシージャまたはブロック内ではなく)、モジュール レベルで変数を宣言する使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="bfa22-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="bfa22-111">場合`num2`前の例では、プロシージャ内のローカル変数ではなくクラスのフィールドでエラーが発生すると、宣言`Option Strict`、および分類は`num2`として、`Object`と`Option Strict`オフします。</span><span class="sxs-lookup"><span data-stu-id="bfa22-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="bfa22-112">同様に、ローカル型の推論には当てはまりませんプロシージャ レベルの変数として宣言されている`Static`します。</span><span class="sxs-lookup"><span data-stu-id="bfa22-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>  
  
## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="bfa22-113">型の推論と遅延バインディング</span><span class="sxs-lookup"><span data-stu-id="bfa22-113">Type Inference vs. Late Binding</span></span>  
 <span data-ttu-id="bfa22-114">推論タイプをコードでは、遅延バインディングに依存するコードに似ています。</span><span class="sxs-lookup"><span data-stu-id="bfa22-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="bfa22-115">ただし、型の推論型を厳密として残さず変数`Object`します。</span><span class="sxs-lookup"><span data-stu-id="bfa22-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="bfa22-116">コンパイラでは、変数の初期化子を使用して、事前バインディングされたコードを作成するコンパイル時に、変数の型を調べます。</span><span class="sxs-lookup"><span data-stu-id="bfa22-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="bfa22-117">前の例で`num2`と同様に`num1`、として型指定された、`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="bfa22-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>  
  
 <span data-ttu-id="bfa22-118">事前バインディングされた変数の動作は、実行時にのみを型が認識されている、遅延バインディングされた変数の動作とは異なります。</span><span class="sxs-lookup"><span data-stu-id="bfa22-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="bfa22-119">型の早い段階により、コンパイラは、実行前に問題を識別するために理解していれば、正確には、メモリを割り当てし、その他の最適化を実行します。</span><span class="sxs-lookup"><span data-stu-id="bfa22-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="bfa22-120">事前バインディングでは、Visual Basic の統合開発環境 (IDE) のオブジェクトのメンバーについて IntelliSense のヘルプを提供することもできます。</span><span class="sxs-lookup"><span data-stu-id="bfa22-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="bfa22-121">事前バインディングもパフォーマンスの優先的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="bfa22-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="bfa22-122">これは、遅延バインディングされた変数に格納されているすべてのデータは、型としてラップする必要があるために、 `Object`、低速のプログラムは、実行時に、型のメンバーにアクセスするとします。</span><span class="sxs-lookup"><span data-stu-id="bfa22-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bfa22-123">例</span><span class="sxs-lookup"><span data-stu-id="bfa22-123">Examples</span></span>  
 <span data-ttu-id="bfa22-124">型の推定が発生せず、ローカル変数が宣言されている場合、`As`句と初期化します。</span><span class="sxs-lookup"><span data-stu-id="bfa22-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="bfa22-125">コンパイラは、変数の型として割り当てられた初期値の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="bfa22-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="bfa22-126">たとえば、次のコード行の各型の変数を宣言`String`します。</span><span class="sxs-lookup"><span data-stu-id="bfa22-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>  
  
 <span data-ttu-id="bfa22-127">[!code-vb[VbVbalrTypeInference&#2;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="bfa22-127">[!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]</span></span>  
  
 <span data-ttu-id="bfa22-128">次のコードでは、整数の配列を作成する&2; つの同等の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bfa22-128">The following code demonstrates two equivalent ways to create an array of integers.</span></span>  
  
 <span data-ttu-id="bfa22-129">[!code-vb[VbVbalrTypeInference&#3;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="bfa22-129">[!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]</span></span>  
  
 <span data-ttu-id="bfa22-130">型の推論を使用して、ループ制御変数の型を確認すると便利です。</span><span class="sxs-lookup"><span data-stu-id="bfa22-130">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="bfa22-131">次のコードに、コンパイラが推論される`number`は、`Integer`ため`someNumbers2`前の例は、整数の配列。</span><span class="sxs-lookup"><span data-stu-id="bfa22-131">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>  
  
 <span data-ttu-id="bfa22-132">[!code-vb[VbVbalrTypeInference&4;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="bfa22-132">[!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]</span></span>  
  
 <span data-ttu-id="bfa22-133">ローカル型推論を使用できる`Using`ステートメントを次の例に示すように、リソース名の型を設定します。</span><span class="sxs-lookup"><span data-stu-id="bfa22-133">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>  
  
 <span data-ttu-id="bfa22-134">[!code-vb[VbVbalrTypeInference&#7;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="bfa22-134">[!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]</span></span>  
  
 <span data-ttu-id="bfa22-135">次の例に示すように、変数の型を関数の戻り値から推論もことができます。</span><span class="sxs-lookup"><span data-stu-id="bfa22-135">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="bfa22-136">両方とも`pList1`と`pList2`ためのプロセスの配列である`Process.GetProcesses`プロセスの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="bfa22-136">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>  
  
 <span data-ttu-id="bfa22-137">[!code-vb[VbVbalrTypeInference&#5;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="bfa22-137">[!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]</span></span>  
  
## <a name="option-infer"></a><span data-ttu-id="bfa22-138">Option Infer します。</span><span class="sxs-lookup"><span data-stu-id="bfa22-138">Option Infer</span></span>  
 <span data-ttu-id="bfa22-139">`Option Infer`特定のファイルでローカル型推論を許可するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bfa22-139">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="bfa22-140">有効にするか、オプションは、ファイルの先頭に次のステートメントのいずれかを入力します。</span><span class="sxs-lookup"><span data-stu-id="bfa22-140">To enable or to block the option, type one of the following statements at the start of the file.</span></span>  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 <span data-ttu-id="bfa22-141">値が指定されていない場合`Option Infer`コンパイラの既定値は、コードでは、`Option Infer On`です。</span><span class="sxs-lookup"><span data-stu-id="bfa22-141">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span> <span data-ttu-id="bfa22-142">アップグレードされたプロジェクトの[!INCLUDE[vb_orcas_long](../../../../visual-basic/misc/includes/vb_orcas_long_md.md)]コンパイラの既定値は、前の手順では、または`Option Infer Off`です。</span><span class="sxs-lookup"><span data-stu-id="bfa22-142">For projects upgraded from [!INCLUDE[vb_orcas_long](../../../../visual-basic/misc/includes/vb_orcas_long_md.md)] or earlier, the compiler default is `Option Infer Off`.</span></span>  
  
 <span data-ttu-id="bfa22-143">ファイルの `Option Infer` に設定した値が IDE またはコマンド ラインに設定した値と競合した場合は、ファイルの値が優先されます。</span><span class="sxs-lookup"><span data-stu-id="bfa22-143">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="bfa22-144">詳細については、次を参照してください。 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)と[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="bfa22-144">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="bfa22-145">制限事項</span><span class="sxs-lookup"><span data-stu-id="bfa22-145">Restrictions</span></span>  
 <span data-ttu-id="bfa22-146">型の推論は、非静的ローカル変数に対してのみ使用できます。クラスのフィールド、プロパティ、または関数の種類を判断に使用できません。</span><span class="sxs-lookup"><span data-stu-id="bfa22-146">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfa22-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="bfa22-147">See Also</span></span>  
 <span data-ttu-id="bfa22-148">[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="bfa22-148">[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="bfa22-149"> [事前バインディングと遅延バインディング](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md) </span><span class="sxs-lookup"><span data-stu-id="bfa22-149"> [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md) </span></span>  
<span data-ttu-id="bfa22-150"> [各.次のステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="bfa22-150"> [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span></span>  
<span data-ttu-id="bfa22-151"> [.次のステートメント](../../../../visual-basic/language-reference/statements/for-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="bfa22-151"> [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md) </span></span>  
<span data-ttu-id="bfa22-152"> [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="bfa22-152"> [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="bfa22-153"> [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="bfa22-153"> [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="bfa22-154"> [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="bfa22-154"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
