---
title: "Visual Basic における文字列の基本"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8881ad6ab7f28689019463abdab3b867e010d51e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="9fbb0-102">Visual Basic における文字列の基本</span><span class="sxs-lookup"><span data-stu-id="9fbb0-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="9fbb0-103">`String` データ型は、一連の文字を表します (各文字は `Char` データ型のインスタンスを表しています)。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="9fbb0-104">このトピックでは、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] での文字列の基本的な概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-104">This topic introduces the basic concepts of strings in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="9fbb0-105">文字列変数</span><span class="sxs-lookup"><span data-stu-id="9fbb0-105">String Variables</span></span>  
 <span data-ttu-id="9fbb0-106">文字列のインスタンスには、一連の文字を表すリテラル値を代入できます。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="9fbb0-107">例:</span><span class="sxs-lookup"><span data-stu-id="9fbb0-107">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]  
  
 <span data-ttu-id="9fbb0-108">`String` 変数は、文字列に評価される任意の式も受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-108">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="9fbb0-109">以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-109">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]  
  
 <span data-ttu-id="9fbb0-110">`String` 変数に代入されるすべてのリテラルは、引用符 ("") で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-110">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="9fbb0-111">これは、文字列内の引用符を引用符で表すことができないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-111">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="9fbb0-112">たとえば、次のコードはコンパイラ エラーになります。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-112">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]  
  
 <span data-ttu-id="9fbb0-113">このコードでは、2 つ目の引用符の後で文字列が終了し、残りの部分はコードであるとコンパイラが解釈するため、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-113">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="9fbb0-114">この問題を解決するために、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] は文字列リテラル内の 2 つの引用符を文字列内の 1 つの引用符として解釈します。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-114">To solve this problem, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="9fbb0-115">次の例は、引用符を文字列に含めるための正しい方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-115">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]  
  
 <span data-ttu-id="9fbb0-116">前の例で、`Look` という単語の前の 2 つの引用符は、文字列内では 1 つの引用符になります。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-116">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="9fbb0-117">行の末尾の 3 つの引用符は、文字列内の 1 つの引用符と文字列終端文字を表します。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-117">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="9fbb0-118">文字列リテラルには、複数の行を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-118">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="9fbb0-119">結果の文字列には、文字列リテラルで使用する改行シーケンス (vbcr、vbcrlf など) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-119">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="9fbb0-120">古い回避策を使用する必要はなくなりました。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-120">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="9fbb0-121">文字列内の文字</span><span class="sxs-lookup"><span data-stu-id="9fbb0-121">Characters in Strings</span></span>  
 <span data-ttu-id="9fbb0-122">文字列は、一連の `Char` 値であると考えることができます。また、配列の場合と同様に、`String` 型には文字列に対してさまざまな操作を行うことができる、組み込み関数があります。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-122">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="9fbb0-123">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] のすべての配列のように、これらは 0 ベース配列です。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-123">Like all array in [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], these are zero-based arrays.</span></span> <span data-ttu-id="9fbb0-124">文字列内の特定の文字は、`Chars` プロパティを通じて参照できます。このプロパティでは、文字列内で文字が現れる位置を使用して、文字にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-124">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="9fbb0-125">例:</span><span class="sxs-lookup"><span data-stu-id="9fbb0-125">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]  
  
 <span data-ttu-id="9fbb0-126">上の例で、文字列の `Chars` プロパティは、文字列内の 4 番目の文字 (つまり `D`) を返し、`myChar` に代入します。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-126">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="9fbb0-127">`Length` プロパティを通じて、特定の文字列の長さを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-127">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="9fbb0-128">文字列に対して複数の配列型の操作を実行する必要がある場合は、文字列の `ToCharArray` 関数を使用して、文字列を `Char` インスタンスの配列に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-128">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="9fbb0-129">例:</span><span class="sxs-lookup"><span data-stu-id="9fbb0-129">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]  
  
 <span data-ttu-id="9fbb0-130">これで、変数 `myArray` の内容は、`Char` 値の配列になりました。各値は `myString` の文字を表しています。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-130">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="9fbb0-131">文字列の不変性</span><span class="sxs-lookup"><span data-stu-id="9fbb0-131">The Immutability of Strings</span></span>  
 <span data-ttu-id="9fbb0-132">文字列は*不変*つまり、その値を 1 回変更することはできませんが作成されました。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-132">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="9fbb0-133">ただし、文字列変数に複数の値を代入できないわけではありません。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-133">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="9fbb0-134">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-134">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]  
  
 <span data-ttu-id="9fbb0-135">ここでは、文字列変数が作成され、値を設定され、その値が変更されています。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-135">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="9fbb0-136">より具体的には、最初の行で型 `String` のインスタンスが作成され、値 `This string is immutable` が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-136">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="9fbb0-137">例の 2 番目の行では、新しいインスタンスが作成され、値 `Or is it?` が設定されます。文字列変数は、最初のインスタンスへの参照を破棄し、新しいインスタンスへの参照を格納します。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-137">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="9fbb0-138">他の組み込みのデータ型とは異なり、`String` は参照型です。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-138">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="9fbb0-139">参照型の変数が関数またはサブルーチンへの引数として渡されると、文字列の実際の値ではなく、データが格納されているメモリ アドレスへの参照が渡されます。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-139">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="9fbb0-140">そのため、前の例では変数の名前は変わりませんが、新しい値を保持している、`String` クラスの新しい別のインスタンスを指すようになります。</span><span class="sxs-lookup"><span data-stu-id="9fbb0-140">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fbb0-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fbb0-141">See Also</span></span>  
 [<span data-ttu-id="9fbb0-142">Visual Basic の文字列の概要</span><span class="sxs-lookup"><span data-stu-id="9fbb0-142">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [<span data-ttu-id="9fbb0-143">String データ型</span><span class="sxs-lookup"><span data-stu-id="9fbb0-143">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="9fbb0-144">Char データ型</span><span class="sxs-lookup"><span data-stu-id="9fbb0-144">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [<span data-ttu-id="9fbb0-145">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="9fbb0-145">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
