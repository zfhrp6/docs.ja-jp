---
title: "Visual Basic における基本文字列 |Microsoft ドキュメント"
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
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
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
ms.openlocfilehash: 98c2707ef8aabc77951b21cfe9f4edcd3a88c863
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="1035c-102">Visual Basic における文字列の基本</span><span class="sxs-lookup"><span data-stu-id="1035c-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="1035c-103">`String` データ型は、一連の文字を表します (各文字は `Char` データ型のインスタンスを表しています)。</span><span class="sxs-lookup"><span data-stu-id="1035c-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="1035c-104">このトピックでは、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] での文字列の基本的な概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="1035c-104">This topic introduces the basic concepts of strings in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="1035c-105">文字列変数</span><span class="sxs-lookup"><span data-stu-id="1035c-105">String Variables</span></span>  
 <span data-ttu-id="1035c-106">文字列のインスタンスには、一連の文字を表すリテラル値を代入できます。</span><span class="sxs-lookup"><span data-stu-id="1035c-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="1035c-107">例:</span><span class="sxs-lookup"><span data-stu-id="1035c-107">For example:</span></span>  
  
 <span data-ttu-id="1035c-108">[!code-vb[VbVbalrStrings #&63;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1035c-108">[!code-vb[VbVbalrStrings#63](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]</span></span>  
  
 <span data-ttu-id="1035c-109">`String` 変数は、文字列に評価される任意の式も受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="1035c-109">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="1035c-110">以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1035c-110">Examples are shown below:</span></span>  
  
 <span data-ttu-id="1035c-111">[!code-vb[VbVbalrStrings #&64;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="1035c-111">[!code-vb[VbVbalrStrings#64](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]</span></span>  
  
 <span data-ttu-id="1035c-112">`String` 変数に代入されるすべてのリテラルは、引用符 ("") で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="1035c-112">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="1035c-113">これは、文字列内の引用符を引用符で表すことができないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="1035c-113">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="1035c-114">たとえば、次のコードはコンパイラ エラーになります。</span><span class="sxs-lookup"><span data-stu-id="1035c-114">For example, the following code causes a compiler error:</span></span>  
  
 <span data-ttu-id="1035c-115">[!code-vb[VbVbalrStrings #&65;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="1035c-115">[!code-vb[VbVbalrStrings#65](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]</span></span>  
  
 <span data-ttu-id="1035c-116">このコードでは、2 つ目の引用符の後で文字列が終了し、残りの部分はコードであるとコンパイラが解釈するため、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="1035c-116">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="1035c-117">この問題を解決するために、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は文字列リテラル内の&2; つの引用符を文字列内の&1; つの引用符として解釈します。</span><span class="sxs-lookup"><span data-stu-id="1035c-117">To solve this problem, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="1035c-118">次の例は、引用符を文字列に含めるための正しい方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1035c-118">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 <span data-ttu-id="1035c-119">[!code-vb[VbVbalrStrings #&66;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="1035c-119">[!code-vb[VbVbalrStrings#66](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]</span></span>  
  
 <span data-ttu-id="1035c-120">前の例で、`Look` という単語の前の&2; つの引用符は、文字列内では&1; つの引用符になります。</span><span class="sxs-lookup"><span data-stu-id="1035c-120">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="1035c-121">行の末尾の&3; つの引用符は、文字列内の&1; つの引用符と文字列終端文字を表します。</span><span class="sxs-lookup"><span data-stu-id="1035c-121">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="1035c-122">文字列リテラルには、複数の行を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="1035c-122">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
  
```  
  
 <span data-ttu-id="1035c-123">結果の文字列には、文字列リテラルで使用する改行シーケンス (vbcr、vbcrlf など) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1035c-123">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="1035c-124">古い回避策を使用する必要はなくなりました。</span><span class="sxs-lookup"><span data-stu-id="1035c-124">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="1035c-125">文字列内の文字</span><span class="sxs-lookup"><span data-stu-id="1035c-125">Characters in Strings</span></span>  
 <span data-ttu-id="1035c-126">文字列は、一連の `Char` 値であると考えることができます。また、配列の場合と同様に、`String` 型には文字列に対してさまざまな操作を行うことができる、組み込み関数があります。</span><span class="sxs-lookup"><span data-stu-id="1035c-126">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="1035c-127">[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] のすべての配列のように、これらは&0; ベース配列です。</span><span class="sxs-lookup"><span data-stu-id="1035c-127">Like all array in [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)], these are zero-based arrays.</span></span> <span data-ttu-id="1035c-128">文字列内の特定の文字は、`Chars` プロパティを通じて参照できます。このプロパティでは、文字列内で文字が現れる位置を使用して、文字にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1035c-128">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="1035c-129">例:</span><span class="sxs-lookup"><span data-stu-id="1035c-129">For example:</span></span>  
  
 <span data-ttu-id="1035c-130">[!code-vb[VbVbalrStrings #&67;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="1035c-130">[!code-vb[VbVbalrStrings#67](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]</span></span>  
  
 <span data-ttu-id="1035c-131">上の例で、文字列の `Chars` プロパティは、文字列内の&4; 番目の文字 (つまり `D`) を返し、`myChar` に代入します。</span><span class="sxs-lookup"><span data-stu-id="1035c-131">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="1035c-132">`Length` プロパティを通じて、特定の文字列の長さを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="1035c-132">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="1035c-133">文字列に対して複数の配列型の操作を実行する必要がある場合は、文字列の `ToCharArray` 関数を使用して、文字列を `Char` インスタンスの配列に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="1035c-133">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="1035c-134">例:</span><span class="sxs-lookup"><span data-stu-id="1035c-134">For example:</span></span>  
  
 <span data-ttu-id="1035c-135">[!code-vb[VbVbalrStrings #&68;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="1035c-135">[!code-vb[VbVbalrStrings#68](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]</span></span>  
  
 <span data-ttu-id="1035c-136">これで、変数 `myArray` の内容は、`Char` 値の配列になりました。各値は `myString` の文字を表しています。</span><span class="sxs-lookup"><span data-stu-id="1035c-136">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="1035c-137">文字列の不変性</span><span class="sxs-lookup"><span data-stu-id="1035c-137">The Immutability of Strings</span></span>  
 <span data-ttu-id="1035c-138">文字列とは、*不変*つまり、その値を一度変更することはできませんが作成されました。</span><span class="sxs-lookup"><span data-stu-id="1035c-138">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="1035c-139">ただし、文字列変数に複数の値を代入できないわけではありません。</span><span class="sxs-lookup"><span data-stu-id="1035c-139">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="1035c-140">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1035c-140">Consider the following example:</span></span>  
  
 <span data-ttu-id="1035c-141">[!code-vb[VbVbalrStrings #&69;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="1035c-141">[!code-vb[VbVbalrStrings#69](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]</span></span>  
  
 <span data-ttu-id="1035c-142">ここでは、文字列変数が作成され、値を設定され、その値が変更されています。</span><span class="sxs-lookup"><span data-stu-id="1035c-142">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="1035c-143">より具体的には、最初の行で型 `String` のインスタンスが作成され、値 `This string is immutable` が設定されます。</span><span class="sxs-lookup"><span data-stu-id="1035c-143">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="1035c-144">例の&2; 番目の行では、新しいインスタンスが作成され、値 `Or is it?` が設定されます。文字列変数は、最初のインスタンスへの参照を破棄し、新しいインスタンスへの参照を格納します。</span><span class="sxs-lookup"><span data-stu-id="1035c-144">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="1035c-145">他の組み込みのデータ型とは異なり、`String` は参照型です。</span><span class="sxs-lookup"><span data-stu-id="1035c-145">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="1035c-146">参照型の変数が関数またはサブルーチンへの引数として渡されると、文字列の実際の値ではなく、データが格納されているメモリ アドレスへの参照が渡されます。</span><span class="sxs-lookup"><span data-stu-id="1035c-146">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="1035c-147">そのため、前の例では変数の名前は変わりませんが、新しい値を保持している、`String` クラスの新しい別のインスタンスを指すようになります。</span><span class="sxs-lookup"><span data-stu-id="1035c-147">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1035c-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="1035c-148">See Also</span></span>  
 <span data-ttu-id="1035c-149">[Visual Basic における文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md) </span><span class="sxs-lookup"><span data-stu-id="1035c-149">[Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md) </span></span>  
<span data-ttu-id="1035c-150"> [文字列データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="1035c-150"> [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span></span>  
<span data-ttu-id="1035c-151"> [Char データ型](../../../../visual-basic/language-reference/data-types/char-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="1035c-151"> [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md) </span></span>  
<span data-ttu-id="1035c-152"> [基本的な文字列操作](http://msdn.microsoft.com/library/8133d357-90b5-4b62-9927-43323d99b6b6)</span><span class="sxs-lookup"><span data-stu-id="1035c-152"> [Basic String Operations](http://msdn.microsoft.com/library/8133d357-90b5-4b62-9927-43323d99b6b6)</span></span>
