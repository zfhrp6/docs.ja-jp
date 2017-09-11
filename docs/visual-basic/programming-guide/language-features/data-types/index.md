---
title: "Visual Basic におけるデータ型"
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
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8b90a5e58d135a3769761ca431fd0c05f79e045f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="data-types-in-visual-basic"></a><span data-ttu-id="9802c-102">Visual Basic におけるデータ型</span><span class="sxs-lookup"><span data-stu-id="9802c-102">Data Types in Visual Basic</span></span>
<span data-ttu-id="9802c-103">プログラミング要素の*データ型*は、保持できるデータの種類やデータの格納方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9802c-103">The *data type* of a programming element refers to what kind of data it can hold and how it stores that data.</span></span> <span data-ttu-id="9802c-104">データ型は、コンピューターのメモリに格納できるすべての値に適用され、式の評価にも関与します。</span><span class="sxs-lookup"><span data-stu-id="9802c-104">Data types apply to all values that can be stored in computer memory or participate in the evaluation of an expression.</span></span> <span data-ttu-id="9802c-105">変数、リテラル、定数、列挙値、プロパティ、プロシージャのパラメーター、プロシージャの引数、およびプロシージャの戻り値にはすべてデータ型があります。</span><span class="sxs-lookup"><span data-stu-id="9802c-105">Every variable, literal, constant, enumeration, property, procedure parameter, procedure argument, and procedure return value has a data type.</span></span>  
  
## <a name="declared-data-types"></a><span data-ttu-id="9802c-106">宣言済みデータ型</span><span class="sxs-lookup"><span data-stu-id="9802c-106">Declared Data Types</span></span>  
 <span data-ttu-id="9802c-107">プログラミング要素は、宣言ステートメントで定義し、`As` 句を使用してデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="9802c-107">You define a programming element with a declaration statement, and you specify its data type with the `As` clause.</span></span> <span data-ttu-id="9802c-108">次の表は、さまざまな要素の宣言に使用するステートメントを示しています。</span><span class="sxs-lookup"><span data-stu-id="9802c-108">The following table shows the statements you use to declare various elements.</span></span>  
  
|<span data-ttu-id="9802c-109">プログラミング要素</span><span class="sxs-lookup"><span data-stu-id="9802c-109">Programming element</span></span>|<span data-ttu-id="9802c-110">データ型の宣言</span><span class="sxs-lookup"><span data-stu-id="9802c-110">Data type declaration</span></span>|  
|-------------------------|---------------------------|  
|<span data-ttu-id="9802c-111">変数</span><span class="sxs-lookup"><span data-stu-id="9802c-111">Variable</span></span>|<span data-ttu-id="9802c-112">[Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="9802c-112">In a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)</span></span><br /><br /> <span data-ttu-id="9802c-113">`Dim`   `amount As Double`</span><span class="sxs-lookup"><span data-stu-id="9802c-113">`Dim`   `amount As Double`</span></span><br /><br /> <span data-ttu-id="9802c-114">`Static`   `yourName As String`</span><span class="sxs-lookup"><span data-stu-id="9802c-114">`Static`   `yourName As String`</span></span><br /><br /> <span data-ttu-id="9802c-115">`Public`   `billsPaid As Decimal = 0`</span><span class="sxs-lookup"><span data-stu-id="9802c-115">`Public`   `billsPaid As Decimal = 0`</span></span>|  
|<span data-ttu-id="9802c-116">Literal</span><span class="sxs-lookup"><span data-stu-id="9802c-116">Literal</span></span>|<span data-ttu-id="9802c-117">リテラルの型文字で指定する場合は、「[Type Characters (型文字)](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)」の「Literal Type Characters (リテラルの型文字)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="9802c-117">With a literal type character; see "Literal Type Characters" in [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span></span><br /><br /> <span data-ttu-id="9802c-118">`Dim searchChar As Char = "."`  `C`</span><span class="sxs-lookup"><span data-stu-id="9802c-118">`Dim searchChar As Char = "."`  `C`</span></span>|  
|<span data-ttu-id="9802c-119">定数</span><span class="sxs-lookup"><span data-stu-id="9802c-119">Constant</span></span>|<span data-ttu-id="9802c-120">[Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)</span><span class="sxs-lookup"><span data-stu-id="9802c-120">In a [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)</span></span><br /><br /> <span data-ttu-id="9802c-121">`Const`   `modulus As Single = 4.17825F`</span><span class="sxs-lookup"><span data-stu-id="9802c-121">`Const`   `modulus As Single = 4.17825F`</span></span>|  
|<span data-ttu-id="9802c-122">列挙</span><span class="sxs-lookup"><span data-stu-id="9802c-122">Enumeration</span></span>|<span data-ttu-id="9802c-123">[Enum ステートメント](../../../../visual-basic/language-reference/statements/enum-statement.md)</span><span class="sxs-lookup"><span data-stu-id="9802c-123">In an [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md)</span></span><br /><br /> <span data-ttu-id="9802c-124">`Public`   `Enum`   `colors`</span><span class="sxs-lookup"><span data-stu-id="9802c-124">`Public`   `Enum`   `colors`</span></span>|  
|<span data-ttu-id="9802c-125">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9802c-125">Property</span></span>|<span data-ttu-id="9802c-126">[Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)</span><span class="sxs-lookup"><span data-stu-id="9802c-126">In a [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)</span></span><br /><br /> <span data-ttu-id="9802c-127">`Property`   `region() As String`</span><span class="sxs-lookup"><span data-stu-id="9802c-127">`Property`   `region() As String`</span></span>|  
|<span data-ttu-id="9802c-128">プロシージャ パラメーター</span><span class="sxs-lookup"><span data-stu-id="9802c-128">Procedure parameter</span></span>|<span data-ttu-id="9802c-129">[Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)、[Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)、または[Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)</span><span class="sxs-lookup"><span data-stu-id="9802c-129">In a [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md), [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md), or [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)</span></span><br /><br /> <span data-ttu-id="9802c-130">`Sub addSale(ByVal`   `amount`   `As Double)`</span><span class="sxs-lookup"><span data-stu-id="9802c-130">`Sub addSale(ByVal`   `amount`   `As Double)`</span></span>|  
|<span data-ttu-id="9802c-131">プロシージャ引数</span><span class="sxs-lookup"><span data-stu-id="9802c-131">Procedure argument</span></span>|<span data-ttu-id="9802c-132">呼び出しコードの各引数は、すでに宣言されているプログラミング要素、または宣言されている要素を含む式です</span><span class="sxs-lookup"><span data-stu-id="9802c-132">In the calling code; each argument is a programming element that has already been declared, or an expression containing declared elements</span></span><br /><br /> <span data-ttu-id="9802c-133">`subString = Left(`  `inputString`  `,`   `5`  `)`</span><span class="sxs-lookup"><span data-stu-id="9802c-133">`subString = Left(`  `inputString`  `,`   `5`  `)`</span></span>|  
|<span data-ttu-id="9802c-134">プロシージャの戻り値</span><span class="sxs-lookup"><span data-stu-id="9802c-134">Procedure return value</span></span>|<span data-ttu-id="9802c-135">[Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)、または[Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)</span><span class="sxs-lookup"><span data-stu-id="9802c-135">In a [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) or [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)</span></span><br /><br /> <span data-ttu-id="9802c-136">`Function convert(ByVal b As Byte)`   `As String`</span><span class="sxs-lookup"><span data-stu-id="9802c-136">`Function convert(ByVal b As Byte)`   `As String`</span></span>|  
  
 <span data-ttu-id="9802c-137">Visual Basic のデータ型の一覧については、[データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9802c-137">For a list of Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9802c-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="9802c-138">See Also</span></span>  
 <span data-ttu-id="9802c-139">[型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span><span class="sxs-lookup"><span data-stu-id="9802c-139">[Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span></span>  
 <span data-ttu-id="9802c-140">[基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="9802c-140">[Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
 <span data-ttu-id="9802c-141">[複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="9802c-141">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span></span>  
 <span data-ttu-id="9802c-142">[Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="9802c-142">[Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
 <span data-ttu-id="9802c-143">[値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="9802c-143">[Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
 <span data-ttu-id="9802c-144">[Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="9802c-144">[Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
 <span data-ttu-id="9802c-145">[構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="9802c-145">[Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
 <span data-ttu-id="9802c-146">[タプル](tuples.md)   </span><span class="sxs-lookup"><span data-stu-id="9802c-146">[Tuples](tuples.md)   </span></span>  
 <span data-ttu-id="9802c-147">[データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="9802c-147">[Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
 <span data-ttu-id="9802c-148">[データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="9802c-148">[Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
 [<span data-ttu-id="9802c-149">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="9802c-149">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

